// This is a comment 
// ERC721-free-and-paid-mint
// An erc721 contract with a free and paid mint for each wallet 
// SPDX-License-Identifier: MIT
// contract license

pragma solidity ^0.8.2
// solidity version

import "@openzeppelin/contracts/token/ERC721/extensions/ERC721Enumerable.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/Strings.sol";


contract R is ERC721Enumerable, Ownable {
using String for uint256;

// state variable
string baseURI;
string public baseExtension = ".json";
uint256 public cost = 0.002 ether;
uint256 public maxSupply = 3333;
uint256 public maxMintAmount = 5;
bool public pasued = true;
bool public revealed = true;

constructor(
string memory name,
string memory _symbol,
string memory _initBaseURI
) ERC721(name, _symbol) {
baseURI(initBaseURI)
}

=================================
// internal
=================================
function _baseURI() internal view virtual override returns (string memory) {
return baseURI;
}

===============================
// public 
===============================
function mint(uint256 _mintAmount) public payable {
uint256 supply = totalSupply();
require(!paused);
require(_mintamount > 0);
require(_mintAmount <= maxMintAmount);
require(supply + _mintamount <= maxSupply);

if (msg.sender !=owner()) {
require(msg.value== 1) {
_safeMint(msg.sender, supply + 1);
} else {
for (uint256 i = 2; i <= _mintAmount; i++) {
_safeMint(msg.sender, supply + i);
}
}

  function walletOfOwner(address _owner)
    public
    view
    returns (uint256[] memory)
  {
    uint256 ownerTokenCount = balanceOf(_owner);
    uint256[] memory tokenIds = new uint256[](ownerTokenCount);
    for (uint256 i; i < ownerTokenCount; i++) {
      tokenIds[i] = tokenOfOwnerByIndex(_owner, i);
    }
    return tokenIds;
  }

  function tokenURI(uint256 tokenId) public view virtual override returns (string memory) {
    require(_exists(tokenId), "ERC721Metadata: URI query for nonexistent token");
   string memory currentBaseURI = _baseURI();
    return bytes(currentBaseURI).length > 0
      ? string(abi.encodePacked(currentBaseURI, tokenId.toString(), baseExtension)): "";
  }

  //only owner
  function reveal() public onlyOwner {
      revealed = true;
  }
  
  function setCost(uint256 _newCost) public onlyOwner {
    cost = _newCost;
  }

  function setmaxMintAmount(uint256 _newmaxMintAmount) public onlyOwner {
    maxMintAmount = _newmaxMintAmount;
  }

  function setBaseURI(string memory _newBaseURI) public onlyOwner {
    baseURI = _newBaseURI;
  }

  function setBaseExtension(string memory _newBaseExtension) public onlyOwner {
    baseExtension = _newBaseExtension;
  }
 
  function withdraw() public payable onlyOwner {
    // This will pay 5% of  initial sale to the added address.
    =============================================================================
  (bool hs, ) = payable(0x2fb8179c8ca593913A620894e9Be85199c27520E).call{value: address(this).balance * 5 / 100}("");
  require(hs);
    =============================================================================
    
    // This will payout the owner 95% of the contract balance.
    // Do not remove this otherwise you will not be able to withdraw the funds.
=============================================================================
   
  (bool os, ) = payable(owner()).call{value: address(this).balance}("");
  require(os);
    
  =============================================================================
  }
}
