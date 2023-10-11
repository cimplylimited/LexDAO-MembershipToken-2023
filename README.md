# LexDAO-MembershipToken-2023
An outline of the current workflow to deploy a simple custom 2023 ERC 721 NFT Token

# Plan Overview
-----------------
## Core Script Files
[LexDAO Token Generator](https://github.com/cimplylimited/file-processing-scripts)


## Base Minting Needs
  - [x] Create a json seed file for the NFT 
  - [x] Create an image seed file for the NFT
  - [x] Create a script to duplicate and increment the json seed file
  - [x] Create a script to increment the Token ID inside the json seed file
    - [ ] can this be done with a smart application using a smart contract or offline process?
    - [ ] ideal is for this to generate the file metadata at mint by interacting with an off-chain application 
  - [ ] Create a script to convert the NFT seed file to base-64
  - [x] Pull a template open-zepplin minting contract
  - [ ] Edit parameters of the open-zepplin minting contract to include
    - [ ] Enumeratability
    - [ ] Burn Function
    - [ ] Non-Transferrability
    - [ ] Time expiration
      - [ ] Considerations for the ERC-4907
        - Remember that in this standard the token remains the property of the origin rather than the "renter"
      - [ ] Second Consideration is to embed the token with a time value in the contract itself using a store variable in solidity.  Would like this to be an explicit value updateable by the admin minting wallet.    
  - [ ] Transfer ownership of the contract to the DAO Gnosis Safe for minting
    - [ ] This may be a sub-wallet with approvals or might be a full self-mint
    - [ ] Make sure to include conditions for one mint one wallet
    - [ ] Should we consider ERC-712 authentication?
  - [ ] Test Mint the token
  - [ ] Submit the code for membership review
  - [ ] Formally mint the token
  - [ ] Connect the token to snapshot
  - [ ] Audit the current 2022 membership token for expiration
  - [ ] Grandfather in relevant members per Operating System Document
  
## Transactional Considerations
We will likely need the contract to manage multiple currencies in order to authorize the mint.  For simplicity sake, we should consider implementing the contract with an ability to
  1. connect to etherium blockchain and quote the current usd to eth conversion
  2. standardize the fee based on this calculation at mint in USD
  3. allow for an equivalent in DAI

No other cryptocurrencies to be accepted in **MVP**

### Vesting Period
 - We may want to consider a vesting period for voting rights for paid members
  - See: "Governance Considerations of Smart Contracts for DAO"


## Functional Considerations
 - Given the limitations of some of the true "expiring" values in the meta data for NFTs we will likely need to split a commemorative token/NFT for each year a member is in the DAO with the permissions based "rental" token or other to satisfy the "member card". 
  - The other option here is to figure out how to get the token factory to update the meta data and it's expiration as part of either the contract store value or the actual file generator for the token mints
  - Do we have a way to store contract terms and conditions so that when the contract is called the plain text version of the user T&Cs is able to be visible in the wallet for signature?

### Idea

 - What if we had the contract prebuilt to create the token for a user and then execute a time lock where the token was automatically burned by the smart contract after 365 days.  I would prefer the expiration was just explicit and the artifact continued, but we could either do a rental or a burn and issue a commemorative (either at mint or at burn).
 


  ## Token Asset Value
  ### What does a token represent in LexDAO?
  - LexDAO Tenure: How long you have been a member
  - LexDAO Continuity: What interruptions may have occurred in your tenure
  - Voting Power: LexDAO is and always will be 1 member 1 vote
  - Permissions: Tiers of membership authority centered around
    - Applied and Paid
    - Applied and Work for Member
    - Full Membership
    - Lex Certified
    - Committee Manager
    - Operations (Board) Director



  ## Contract Risk Checks
  In order to help begin the process of trying to minimize risk factors, the following are some checks that we will be trying to build into the contract mint protocol
  - [ ] OFAC Sanction List checks
  - [ ] Flash Loan vulnerabilities
    - [ ] Don't measure governance power in the current block
  - [ ] Check arbitrary data calls in governance
    - [ ] Check success conditions
    - [ ] Re-entrance issues
    - [ ] Return Data
    - [ ] EOA vs. Account with Code
  - [ ] Ensure that if you need a payer function there is a payer function
  - [ ] Beware of msg.values in batched actions
  - [ ] Build the use of delays and guardians
  - [ ] Perform security assessments (especially with upgrades)

  
  # Membership Flow Mockup -  [Excalidraw link](https://excalidraw.com/#room=2129b2214566ba2e246d,ykrk2lDXqfz4XnEUXArLBQ)
  ![Membership Join Flow](https://user-images.githubusercontent.com/106759485/229314079-b935c399-103d-48dc-9dc1-b703409a6262.png)

 # Governance Considerations of Smart Contracts for DAO
 ! [Open Zepplin Presentation on Security Considerations](https://youtu.be/GbDAmMdmh8Q?feature=shared)
  - Considerations around Administrative Transfer of Powers
  - Ensuring a contract can be upgraded
  - Restrictions around Flash Loans of Governance Tokens
  - Delegation of Voting Power
    - Ensure that the membership can delegate its powers to allow others to continue to govern if they do not want to participate
  - Governance Bypass Functions
  - Whitelisting of Proposers
    - Allow users to propose things even if the proposer does not have governance tokens/power
  
  ## Best Practices
  -  Documentation on process for attack vectors the way that [Uniswap](https://docs.uniswap.org/protocol/concepts/governance/adversarial-circumstances)
    - Proposals to exploit vulnerabilities
    - Collecting enough tokens to force malicious proposals through
    - Flashloans or spam governance
    - Bad Faith Proposals
  
  ## Types of Governance Artifacts
  - Improvement Proposals
    - Change a core function
  - Configuration Changes
    - Change a variable
    
  ## Governance Bodies
  - Mini DAOs can utilize different governance functions in a DAO
  - Guardian Multisig
    - A group that can cancel a transaction that is not in the best interest of the DAO
  
  ## Offchain Functional Considerations
  
  # Reference Documents
  --------------------
  
   - minting guidance: [Avalanche Minting Instructions](https://docs.avax.network/community/tutorials-contest/2021/how-to-mint-erc721-using-openzeppelin/tutorial#getting-metadata-ready-to-be-uploaded-to-decentralized-storage)
   - open-zepplin contract: [Open-Zepplin-721-Contract](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v4.7/contracts/token/ERC721/presets/ERC721PresetMinterPauserAutoId.sol)
   - duplicate file script: [File Duplication Script](https://github.com/cimplylimited/file-processing-scripts/blob/main/file_copy_increment.py)   
   - open-zepplin contract wizard: [Contract Wizard](https://wizard.openzeppelin.com/)
   - ERC-721 Token Documents: [Open Zepplin 721 Official Contract Documentation](https://docs.openzeppelin.com/contracts/4.x/erc721)
   - Non-Transferrable Contract Edit (not audited): [Non-Transferrable Contract Edits](https://forum.openzeppelin.com/t/how-to-create-a-non-transferrable-burnable-erc721/2427)
   - Non-Transferrable Tutorial (needs review): [Soulbound ERC 721 Token Tutorial](https://www.ankr.com/docs/smart-contract-tutorials/non-rentable-soulbound-nft/)
   - JSON Beautifier credit @bestape: [JSON Beautifier](https://jsonbeautifier.org/) 
   - Deploying a Multisig Minter: [Multisig Minter and Defender](https://betterprogramming.pub/theres-a-lot-of-excitement-around-nfts-and-with-good-reason-b7ebc5ecc836)
   - IPFS File Storage (free): [NFT.Storage](https://nft.storage/docs/)
   - Open Zeppelin Contract Security Discussion: [Strategies for Secure Governance with Smart Contracts](https://youtu.be/GbDAmMdmh8Q?feature=shared)
   - Ethereum DAO: [Ethereum DAO Page](https://ethereum.org/en/dao)
   - WithTally: [WithTally Wikipage](https://wiki.withtally.com/docs/other-protocols)


