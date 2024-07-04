# CRYPTO EXPLORER 


## Transaction & Block

```mermaid
graph LR
    subgraph TransactionData["Transaction Data"]
        style TransactionData fill:#FFF2CC,stroke:#D6B656
        TransactionDetails["Transaction Details<br/>(Sender, Recipient, Amount)"]
    end

    subgraph Keys["Keys"]
        style Keys fill:#C2E0C6,stroke:#5FB483
        PrivateKey["Private Key (Sender)"]
        PublicKey["Public Key (Sender/Recipient)"]
    end
    PrivateKey --"Signs"--> TransactionSignature
    PublicKey --"Verifies"--> TransactionSignature
    TransactionDetails --"Included in"--> Transaction

    subgraph Transaction["Transaction"]
      style Transaction fill:#E1D5E7,stroke:#9673A6
      TransactionSignature["Digital Signature"]
    end

    subgraph Verification["Verification"]
      style Verification fill:#D4EDDA,stroke:#4CAF50
      BlockchainNetwork["Blockchain Network"]
    end

    Transaction --"Verified by"--> BlockchainNetwork


    subgraph Block["Block (Example)"]
        style Block fill:#F0F0F0,stroke:#888888
        BlockHeader["Block Header"]
        BlockData["Block Data (Multiple Transactions)"]
    end

    Transaction -.-> BlockData
    BlockHeader --> BlockHash["Block Hash"]
    BlockHeader --> PreviousBlockHash["Previous Block's Hash"]
    BlockHeader --> Nonce["Nonce"]
```

## Miner & Node & Wallet

```mermaid
graph LR
    subgraph Network["Blockchain Network"]
        style Network fill:#F2F2F2,stroke:#666666
        Transactions["Transactions"]
        style Transactions fill:#E1D5E7,stroke:#9673A6
        Blocks["Blocks"]
        style Blocks fill:#F0F0F0,stroke:#888888
    end

    subgraph Participants["Participants"]
        style Participants fill:#F0F0F0,stroke:#888888
        Wallet["Wallet (User)"]
        style Wallet fill:#FFF2CC,stroke:#D6B656
        Node["Node"]
        style Node fill:#C2E0C6,stroke:#5FB483
        Miner["Miner"]
        style Miner fill:#F5DEB3,stroke:#D2B48C
    end
    
    subgraph Wallet
      PublicKey["Public Key (Sender/Recipient)"]
      PrivateKey["Private Key (Sender)"]
    end


    Wallet -- "Creates/Receives" --> Transactions
    Node -- "Validates/Stores" --> Transactions
    Node -- "Validates/Stores" --> Blocks
    Miner -- "Creates/Validates" --> Blocks
    Transactions -.-> Blocks

    PrivateKey -- "Signs" --> Transactions
    PublicKey -- "Verifies" --> Transactions
    Miner -- "Receives Rewards From" --> Blocks

```

## Hashrate

```mermaid
graph LR
    HashRate["BTC Hash Rate<br/>614.42 EH/s"]
    style HashRate fill:#F2F2F2,stroke:#666666
    HashRate -- "Represents" --> TotalNetworkPower["Total Network Computing Power"]
    style TotalNetworkPower fill:#FFDDCC,stroke:#E69966

    TotalNetworkPower -- "Influenced by" --> NumberOfMiners["Number of Miners"]
    style NumberOfMiners fill:#FFF2CC,stroke:#D6B656

    TotalNetworkPower -- "Influenced by" --> MiningHardware["Mining Hardware Efficiency"]
    style MiningHardware fill:#C2E0C6,stroke:#5FB483

    HashRate -- "Determines" --> Difficulty["Mining Difficulty"]
    style Difficulty fill:#E1D5E7,stroke:#9673A6

    HashRate -- "Affects" --> BlockTime["Average Block Time<br/>~10 minutes"]
    style BlockTime fill:#D5E8D4,stroke:#82B366
    
    HashRate -- "Indicates" --> Security["Network Security"]
    style Security fill:#9673A6,stroke:#E1D5E7
```
## ETH (proof of stake)

```mermaid
graph LR
    subgraph Network["Blockchain Network (Ethereum 2.0)"]
        style Network fill:#F2F2F2,stroke:#666666
        Transactions["Transactions"]
        style Transactions fill:#E1D5E7,stroke:#9673A6
        Blocks["Blocks"]
        style Blocks fill:#F0F0F0,stroke:#888888
    end

    subgraph Participants["Participants"]
        style Participants fill:#F0F0F0,stroke:#888888
        Wallet["Wallet (User)"]
        style Wallet fill:#FFF2CC,stroke:#D6B656
        Node["Node"]
        style Node fill:#C2E0C6,stroke:#5FB483
        Validator["Validator"]
        style Validator fill:#F5DEB3,stroke:#D2B48C
    end
    
    subgraph Wallet
      PublicKey["Public Key (Sender/Recipient)"]
      PrivateKey["Private Key (Sender)"]
    end

    Wallet -- "Creates/Receives" --> Transactions
    Node -- "Validates/Stores" --> Transactions
    Node -- "Validates/Stores" --> Blocks
    Validator -- "Proposes/Validates" --> Blocks
    Transactions -.-> Blocks

    PrivateKey -- "Signs" --> Transactions
    PublicKey -- "Verifies" --> Transactions
    Validator -- "Receives Rewards From" --> Blocks
    Validator --> StakedETH["Staked ETH (32 ETH)"]
    

```
## Restaking

```mermaid
graph LR
subgraph EthereumBlockchain["Ethereum Blockchain (Beacon Chain)"]
    style EthereumBlockchain fill:#F2F2F2,stroke:#666666
    Validator["Validator"]
    style Validator fill:#FFF2CC,stroke:#D6B656
end

subgraph StakingPlatform["Staking Platform (e.g., Lido)"]
    style StakingPlatform fill:#C2E0C6,stroke:#5FB483
    StakingPool["Staking Pool"]
    style StakingPool fill:#E6F2FF,stroke:#B8D8F2
    stETH["stETH (Liquid Staking Token)"]
    style stETH fill:#D5E8D4,stroke:#82B366
end

subgraph RestakingPlatform["Restaking Platform (e.g., EigenLayer)"]
    style RestakingPlatform fill:#E1D5E7,stroke:#9673A6
    RestakingContract
    style RestakingContract fill:#FFDDCC,stroke:#E69966
    OtherProtocol["Other Protocol/Service"]
    style OtherProtocol fill:#F08080,stroke:#DC143C
end

Validator -- "Stake 32 ETH" --> StakingPool
StakingPool -- "Issues" --> stETH
Validator -- "Receives" --> stETH

stETH -- "Restake" --> RestakingContract
RestakingContract -- "Secures" --> OtherProtocol
RestakingContract -- "Provides" --> AdditionalRewards["Additional Rewards"]

Validator -- "Earns" --> StakingRewards["Staking Rewards (ETH)"]

```
## Smart Contracts

```mermaid
graph LR
    subgraph SmartContract["Smart Contract"]
        style SmartContract fill:#FFF2CC,stroke:#D6B656
        ContractCode["Contract Code<br/>(Solidity, etc.)"]
        StateVariables["State Variables"]
        Functions["Functions"]
        Events["Events"]
    end

    subgraph Blockchain["Blockchain"]
        style Blockchain fill:#F2F2F2,stroke:#666666
        BlockchainNetwork
    end

    subgraph Participants["Participants"]
        style Participants fill:#F0F0F0,stroke:#888888
        User1["User 1"]
        style User1 fill:#C2E0C6,stroke:#5FB483
        User2["User 2"]
        style User2 fill:#F5DEB3,stroke:#D2B48C
    end
    
    subgraph Trigger["Triggers"]
        style Trigger fill:#D4EDDA,stroke:#4CAF50
        ExternalCall["External Call<br/>(User/Contract)"]
        style ExternalCall fill:#E6F2FF,stroke:#B8D8F2
        TimeBased["Time-Based<br/>(e.g., Scheduled Payment)"]
        style TimeBased fill:#E6F2FF,stroke:#B8D8F2
        EventBased["Event-Based<br/>(e.g., Price Change)"]
        style EventBased fill:#E6F2FF,stroke:#B8D8F2
    end


    User1 -- "Interacts With" --> SmartContract
    User2 -- "Interacts With" --> SmartContract

    SmartContract -- "Deployed On" --> BlockchainNetwork
    ContractCode -- "Defines" --> StateVariables
    ContractCode -- "Defines" --> Functions
    ContractCode -- "Defines" --> Events
    Functions -- "Updates" --> StateVariables
    Events -- "Emitted When State Changes" --> BlockchainNetwork

    ExternalCall --> Functions
    TimeBased --> Functions
    EventBased --> Functions

```
### NFT (Non-Fungible Token)

```mermaid
graph LR
    subgraph NFTSmartContract["NFT Smart Contract"]
        style NFTSmartContract fill:#FFF2CC,stroke:#D6B656
        ContractCode["Contract Code<br/>(Solidity, etc.)"]
        StateVariables["State Variables<br/>(Token Metadata, Owner)"]
        Functions["Functions<br/>(Mint, Transfer, Burn)"]
        Events["Events<br/>(Transfer, Approval)"]
    end

    subgraph EthereumBlockchain["Ethereum Blockchain"]
        style EthereumBlockchain fill:#F2F2F2,stroke:#666666
        BlockchainNetwork["Ethereum Network"]
    end

    subgraph Participants["Participants"]
        style Participants fill:#F0F0F0,stroke:#888888
        Creator["Creator"]
        style Creator fill:#C2E0C6,stroke:#5FB483
        Buyer["Buyer"]
        style Buyer fill:#F5DEB3,stroke:#D2B48C
        Seller["Seller"]
        style Seller fill:#ADD8E6,stroke:#4682B4
    end
    
    subgraph Trigger["Triggers"]
        style Trigger fill:#D4EDDA,stroke:#4CAF50
        MintCall["Mint Call<br/>(Creator)"]
        style MintCall fill:#E6F2FF,stroke:#B8D8F2
        TransferCall["Transfer Call<br/>(Owner)"]
        style TransferCall fill:#E6F2FF,stroke:#B8D8F2
        BurnCall["Burn Call<br/>(Owner)"]
        style BurnCall fill:#E6F2FF,stroke:#B8D8F2
    end

    Creator -- "Interacts With" --> NFTSmartContract
    Buyer -- "Interacts With" --> NFTSmartContract
    Seller -- "Interacts With" --> NFTSmartContract

    NFTSmartContract -- "Deployed On" --> BlockchainNetwork
    ContractCode -- "Defines" --> StateVariables
    ContractCode -- "Defines" --> Functions
    ContractCode -- "Defines" --> Events
    Functions -- "Updates" --> StateVariables
    Events -- "Emitted When State Changes" --> BlockchainNetwork

    MintCall --> Functions
    TransferCall --> Functions
    BurnCall --> Functions

```
###  Lending and Borrowing

```mermaid
graph LR
    subgraph DeFiSmartContract["DeFi Lending/Borrowing Smart Contract"]
        style DeFiSmartContract fill:#FFF2CC,stroke:#D6B656
        ContractCode["Contract Code<br/>(Solidity, etc.)"]
        StateVariables["State Variables<br/>(Lender Balances, Borrower Debts)"]
        Functions["Functions<br/>(Deposit, Withdraw, Borrow, Repay)"]
        Events["Events<br/>(Deposit, Withdrawal, Borrow, Repay)"]
    end

    subgraph EthereumBlockchain["Ethereum Blockchain"]
        style EthereumBlockchain fill:#F2F2F2,stroke:#666666
        BlockchainNetwork["Ethereum Network"]
    end

    subgraph Participants["Participants"]
        style Participants fill:#F0F0F0,stroke:#888888
        Lender["Lender"]
        style Lender fill:#C2E0C6,stroke:#5FB483
        Borrower["Borrower"]
        style Borrower fill:#F5DEB3,stroke:#D2B48C
    end
    
    subgraph Trigger["Triggers"]
        style Trigger fill:#D4EDDA,stroke:#4CAF50
        DepositCall["Deposit Call<br/>(Lender)"]
        style DepositCall fill:#E6F2FF,stroke:#B8D8F2
        WithdrawCall["Withdraw Call<br/>(Lender)"]
        style WithdrawCall fill:#E6F2FF,stroke:#B8D8F2
        BorrowCall["Borrow Call<br/>(Borrower)"]
        style BorrowCall fill:#E6F2FF,stroke:#B8D8F2
        RepayCall["Repay Call<br/>(Borrower)"]
        style RepayCall fill:#E6F2FF,stroke:#B8D8F2
    end

    Lender -- "Interacts With" --> DeFiSmartContract
    Borrower -- "Interacts With" --> DeFiSmartContract

    DeFiSmartContract -- "Deployed On" --> BlockchainNetwork
    ContractCode -- "Defines" --> StateVariables
    ContractCode -- "Defines" --> Functions
    ContractCode -- "Defines" --> Events
    Functions -- "Updates" --> StateVariables
    Events -- "Emitted When State Changes" --> BlockchainNetwork

    DepositCall --> Functions
    WithdrawCall --> Functions
    BorrowCall --> Functions
    RepayCall --> Functions

```
## TVL (Total Value Locked)

```mermaid
graph TD
    subgraph DeFiProtocol["DeFi Protocol (e.g., Uniswap, Aave)"]
        style DeFiProtocol fill:#F2F2F2,stroke:#666666
        LiquidityPools["Liquidity Pools"]
        style LiquidityPools fill:#FFF2CC,stroke:#D6B656
        LendingPools["Lending Pools"]
        style LendingPools fill:#E1D5E7,stroke:#9673A6
        StakingContracts["Staking Contracts"]
        style StakingContracts fill:#D5E8D4,stroke:#82B366
    end

    subgraph Assets["Assets (Locked in the Protocol)"]
        style Assets fill:#C2E0C6,stroke:#5FB483
        Crypto1["Crypto Asset 1 (e.g., ETH)"]
        Crypto2["Crypto Asset 2 (e.g., USDC)"]
        Crypto3["Crypto Asset 3 (e.g., WBTC)"]
        LPTokens["LP Tokens (Liquidity Provider Tokens)"]
    end

    subgraph TVL["Total Value Locked (TVL)"]
        style TVL fill:#FFDDCC,stroke:#E69966
        TVLValue["USD Value of All<br/>Locked Assets"]
    end

    Assets --> LiquidityPools
    Assets --> LendingPools
    Assets --> StakingContracts
    LiquidityPools --> TVLValue
    LendingPools --> TVLValue
    StakingContracts --> TVLValue

    TVLValue -- "Indicates" --> ProtocolPopularity["Protocol Popularity"]
    TVLValue -- "Reflects" --> UserTrust["User Trust & Confidence"]
    TVLValue -- "Influences" --> YieldRates["Yield Rates & Incentives"]

```

## Layer 2

```mermaid
graph LR
    subgraph ChildChain["Child Chain"]
        style ChildChain fill:#95E1D3,stroke:#00868B
        ChildBlock1["Block 1"]
        ChildBlock2["Block 2"]
        ChildBlock3["Block 3"]
        ChildBlock1 --> ChildBlock2 --> ChildBlock3
    end

    subgraph ParentChain["Parent Chain"]
        style ParentChain fill:#DCDCDC,stroke:#696969
        ParentBlock1["Block 1"]
        ParentBlock2["Block 2"]
        ParentBlock3["Block 3"]
        ParentBlock1 --> ParentBlock2 --> ParentBlock3
    end

    ChildBlock3 --> Checkpoint["Checkpoint"]
    Checkpoint --> ParentBlock2
```

### Rollup

```mermaid
graph LR
    subgraph RollupChain["Rollup Chain"]
        style RollupChain fill:#FFDDC1,stroke:#FFB6C1
        RollupBlock1["Block 1"]
        RollupBlock2["Block 2"]
        RollupBlock3["Block 3"]
        RollupBlock1 --> RollupBlock2 --> RollupBlock3
    end

    subgraph MainChain["Main Chain"]
        style MainChain fill:#DCDCDC,stroke:#696969
        MainBlock1["Block 1"]
        MainBlock2["Block 2"]
        MainBlock3["Block 3"]
        MainBlock1 --> MainBlock2 --> MainBlock3
    end

    RollupBlock3 --> RollupBatch["Batch of Transactions"]
    RollupBatch --> MainBlock2
    
    RollupTypes["Types of Rollups"] --> OptimisticRollups["Optimistic Rollups"]
    RollupTypes --> ZKRollups["ZK Rollups"]
    OptimisticRollups --> RollupChain
    ZKRollups --> RollupChain
```

## Sharding

```mermaid
graph LR
    subgraph BeaconChain["Beacon Chain"]
        style BeaconChain fill:#F2F2F2,stroke:#666666
        BeaconNode1["Beacon Node 1"]
        BeaconNode2["Beacon Node 2"]
        BeaconNode3["Beacon Node 3"]
        BeaconNode1 --> BeaconNode2
        BeaconNode2 --> BeaconNode3
    end

    subgraph ShardChains["Shard Chains"]
        style ShardChains fill:#C2E0C6,stroke:#5FB483
        ShardChain1["Shard Chain 1"]
        ShardChain2["Shard Chain 2"]
        ShardChain3["Shard Chain 3"]
    end

    BeaconChain --> ShardChain1
    BeaconChain --> ShardChain2
    BeaconChain --> ShardChain3

    subgraph ShardChain1
        style ShardChain1 fill:#E6F2FF,stroke:#B8D8F2
        ShardBlock1["Shard Block 1"]
        ShardBlock2["Shard Block 2"]
        ShardBlock1 --> ShardBlock2
    end

    subgraph ShardChain2
        style ShardChain2 fill:#E6F2FF,stroke:#B8D8F2
        ShardBlock3["Shard Block 3"]
        ShardBlock4["Shard Block 4"]
        ShardBlock3 --> ShardBlock4
    end

    subgraph ShardChain3
        style ShardChain3 fill:#E6F2FF,stroke:#B8D8F2
        ShardBlock5["Shard Block 5"]
        ShardBlock6["Shard Block 6"]
        ShardBlock5 --> ShardBlock6
    end
```