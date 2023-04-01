# LexDAO-MembershipToken-2023
An outline of the current workflow to deploy a simple custom 2023 ERC 721 NFT Token

# Plan Overview
-----------------
  - [x] Create a json seed file for the NFT 
  - [x] Create an image seed file for the NFT
  - [x] Create a script to duplicate and increment the json seed file
  - [ ] Create a script to increment the Token ID inside the json seed file
  - [ ] Create a script to convert the NFT seed file to base-64
  - [x] Pull a template open-zepplin minting contract
  - [ ] Edit parameters of the open-zepplin minting contract to include
    - [ ] Enumeratability
    - [ ] Burn Function
    - [ ] Non-Transferrability
    - [ ] Time expiration
  - [ ] Link the contract to the DAO Safe for minting
  - [ ] Test Mint the token
  - [ ] Submit the code for membership review
  - [ ] Formally mint the token
  - [ ] Connect the token to snapshot
  - [ ] Audit the current 2022 membership token for expiration
  - [ ] Grandfather in relevant members per Operating System Document
  
  
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
