分散型アイデンティティ管理システムを構築してみます。

ここでは、Ethereumブロックチェーン上でDIDを管理し、Next.jsをフロントエンド、NestJSをバックエンド、TypeScriptを共通言語として使用します。
具体的には、Solidityでスマートコントラクトを作成し、Next.jsとNestJSでユーザーインターフェースとAPIを構築します。

### Solidity: スマートコントラクト

まず、DIDを管理するためのスマートコントラクトをSolidityで作成します。

```solidity
// contracts/DIDRegistry.sol
pragma solidity ^0.8.0;

contract DIDRegistry {
    struct DID {
        string didDocument;
        address owner;
    }

    mapping(string => DID) private dids;

    event DIDRegistered(string did, address owner);
    event DIDUpdated(string did, address owner);

    function registerDID(string memory _did, string memory _didDocument) public {
        require(dids[_did].owner == address(0), "DID already registered");
        dids[_did] = DID(_didDocument, msg.sender);
        emit DIDRegistered(_did, msg.sender);
    }

    function updateDID(string memory _did, string memory _didDocument) public {
        require(dids[_did].owner == msg.sender, "Only owner can update DID");
        dids[_did].didDocument = _didDocument;
        emit DIDUpdated(_did, msg.sender);
    }

    function getDIDDocument(string memory _did) public view returns (string memory) {
        require(dids[_did].owner != address(0), "DID not registered");
        return dids[_did].didDocument;
    }
}
```

### TypeScript: TypeScript 型定義

次に、TypeScriptの型定義を作成します。

```typescript
// types/index.d.ts
export interface DID {
    did: string;
    didDocument: string;
    owner: string;
}
```

### NestJS: バックエンド API

NestJSでスマートコントラクトとのやり取りを行うAPIを構築します。

#### モジュールとサービスの設定

```typescript
// src/did/did.module.ts
import { Module } from '@nestjs/common';
import { DIDService } from './did.service';
import { DIDController } from './did.controller';

@Module({
  providers: [DIDService],
  controllers: [DIDController],
})
export class DIDModule {}

// src/did/did.service.ts
import { Injectable } from '@nestjs/common';
import { ethers } from 'ethers';
import { DID } from '../../types';

@Injectable()
export class DIDService {
  private provider: ethers.providers.JsonRpcProvider;
  private contract: ethers.Contract;

  constructor() {
    this.provider = new ethers.providers.JsonRpcProvider('http://localhost:8545');
    const abi = [
      // Add ABI here
    ];
    const address = '0xYourContractAddress';
    this.contract = new ethers.Contract(address, abi, this.provider);
  }

  async registerDID(did: string, didDocument: string, signer: ethers.Signer): Promise<void> {
    const contractWithSigner = this.contract.connect(signer);
    await contractWithSigner.registerDID(did, didDocument);
  }

  async updateDID(did: string, didDocument: string, signer: ethers.Signer): Promise<void> {
    const contractWithSigner = this.contract.connect(signer);
    await contractWithSigner.updateDID(did, didDocument);
  }

  async getDIDDocument(did: string): Promise<string> {
    return await this.contract.getDIDDocument(did);
  }
}

// src/did/did.controller.ts
import { Controller, Get, Post, Body, Param } from '@nestjs/common';
import { DIDService } from './did.service';

@Controller('did')
export class DIDController {
  constructor(private readonly didService: DIDService) {}

  @Post('register')
  async registerDID(@Body() body: { did: string; didDocument: string; privateKey: string }) {
    const signer = new ethers.Wallet(body.privateKey, this.didService.provider);
    await this.didService.registerDID(body.did, body.didDocument, signer);
  }

  @Post('update')
  async updateDID(@Body() body: { did: string; didDocument: string; privateKey: string }) {
    const signer = new ethers.Wallet(body.privateKey, this.didService.provider);
    await this.didService.updateDID(body.did, body.didDocument, signer);
  }

  @Get(':did')
  async getDIDDocument(@Param('did') did: string): Promise<string> {
    return await this.didService.getDIDDocument(did);
  }
}
```

### Next.js: フロントエンド

Next.jsでユーザーインターフェースを作成します。

#### ページとフォームの設定

```javascript
// pages/index.tsx
import { useState } from 'react';
import axios from 'axios';

const Home = () => {
  const [did, setDid] = useState('');
  const [didDocument, setDidDocument] = useState('');
  const [privateKey, setPrivateKey] = useState('');

  const registerDID = async () => {
    await axios.post('/api/did/register', { did, didDocument, privateKey });
  };

  const updateDID = async () => {
    await axios.post('/api/did/update', { did, didDocument, privateKey });
  };

  return (
    <div>
      <h1>DID Manager</h1>
      <input
        type="text"
        placeholder="DID"
        value={did}
        onChange={(e) => setDid(e.target.value)}
      />
      <input
        type="text"
        placeholder="DID Document"
        value={didDocument}
        onChange={(e) => setDidDocument(e.target.value)}
      />
      <input
        type="text"
        placeholder="Private Key"
        value={privateKey}
        onChange={(e) => setPrivateKey(e.target.value)}
      />
      <button onClick={registerDID}>Register DID</button>
      <button onClick={updateDID}>Update DID</button>
    </div>
  );
};

export default Home;
```

#### APIルートの設定

Next.jsのAPIルートを設定して、NestJSのバックエンドと通信します。

```javascript
// pages/api/did/register.ts
import { NextApiRequest, NextApiResponse } from 'next';
import axios from 'axios';

export default async (req: NextApiRequest, res: NextApiResponse) => {
  const { did, didDocument, privateKey } = req.body;
  await axios.post('http://localhost:3000/did/register', { did, didDocument, privateKey });
  res.status(200).end();
};

// pages/api/did/update.ts
import { NextApiRequest, NextApiResponse } from 'next';
import axios from 'axios';

export default async (req: NextApiRequest, res: NextApiResponse) => {
  const { did, didDocument, privateKey } = req.body;
  await axios.post('http://localhost:3000/did/update', { did, didDocument, privateKey });
  res.status(200).end();
};
```

### まとめ

この例では、Ethereum上でDIDを管理するスマートコントラクトをSolidityで作成し、それをNestJSで提供するAPIを介して操作し、Next.jsでユーザーインターフェースを提供しています。この基本的な構造を基に、さらに高度な機能やセキュリティ対策を追加していくことが可能です。

特に、実際のプロジェクトでは以下の点を考慮する必要があります。

- スマートコントラクトのセキュリティ監査。
- フロントエンドとバックエンドの認証とセキュリティ。
- DIDドキュメントのフォーマットと標準に従った実装。
- トランザクションコストの最適化とスケーラビリティの確保。

これにより、分散型アイデンティティ管理システムを実現できます。
