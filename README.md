# LexDAO-MembershipToken-2023
An outline of the current workflow to deploy a simple custom 2023 ERC 721 NFT Token

# Plan Overview
-----------------
  - [x] Create a json seed file for the NFT 
  - [x] Create an image seed file for the NFT
  - [x] Create a script to duplicate and increment the json seed file
  - [] Create a script to increment the Token ID inside the json seed file
  - [] Create a script to convert the NFT seed file to base-64
  - [x] Pull a template open-zepplin minting contract
  - [] Edit parameters of the open-zepplin minting contract to include
    - [] Enumeratability
    - [] Burn Function
    - [] Non-Transferrability
    - [] Time expiration
  - [] Link the contract to the DAO Safe for minting
  - [] Test Mint the token
  - [] Submit the code for membership review
  - [] Formally mint the token
  - [] Connect the token to snapshot
  - [] Audit the current 2022 membership token for expiration
  - [] Grandfather in relevant members per Operating System Document
  
  
  # Reference Documents
  --------------------
  
   - minting guidance: [Avalanche Minting Instructions](https://docs.avax.network/community/tutorials-contest/2021/how-to-mint-erc721-using-openzeppelin/tutorial#getting-metadata-ready-to-be-uploaded-to-decentralized-storage)
   - open-zepplin contract: [Open-Zepplin-721-Contract](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v4.7/contracts/token/ERC721/presets/ERC721PresetMinterPauserAutoId.sol)
   
