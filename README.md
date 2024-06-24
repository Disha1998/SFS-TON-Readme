 # SuperFunSocial


## What problem we are solving?

**We are solving the problem of creators who don't receive real value for their humorous content. They only get "Likes" and "reputation," and have brand deals as their only earning option, while social media platforms capture all the direct monetary value. Funny content can reach millions in no time, but creators get no tangible reward for their humorous content and contribution towards the growth of the platform.**

## Solution
**SuperFunSocial is a social gaming app on Farcaster & Ton where users can earn crypto rewards for creating humorous content such as funny memes and playing games.**

## Key Features
* **Fun Feed:** A place to view and share funny content.
* **Game:** Engage in entertaining games and earn rewards.
* **Store:** Buy and sell digital assets and NFTs.
* **Leaderboard:** Track top performers and compete for the top spot.

## Token Smash

* Token Smash is a game within SuperFunSocial where players can engage in fun and rewarding gameplay.

### Known Issues
  
 * Swipe-Down Gesture in Telegram Mobile App:
      * In the Telegram mobile app, the swipe-down gesture is reserved for minimizing/closing the mini app. So when a user tries to perform a swap in the vertically downward     
             direction, the app attempts to minimize instead. The same works fine in the Telegram web app.

           * **Workaround: Use an upward swipe to perform the swaps. We are looking into the solution for this.**


 * Game Room Closure:
      * When a player leaves the game, sometimes the game room closes after a few seconds. If another player joins the game in this window, it is possible that they may get stuck after the loading bar in the lobby screen is finished loading.

           * **Workaround: Refresh the game. This makes the room get deleted and a new room is created. We are looking into the solution.**
         

* Asset Store in Development:

   * The asset store is in development, so purchases won’t have any effect on the gameplay currently. This will be ready soon.
 

## Instructions

If you’d like to play this in PvP mode, please make sure to join the game as a second player before the timer (indicated by the loading bar at the top of the lobby) runs out.

## Smart Contracts
We have created smart contracts for various functionalities including an NFT collection contract, an NFT item contract for FunPass, and a different NFT contract for GameAsset.

NFT Collection : https://github.com/Disha1998/SFS/blob/main/contracts/nftCollection.tact

FunPass : https://github.com/Disha1998/SFS/blob/main/contracts/nft_item.tact

GameAsset : https://github.com/Disha1998/SFS/blob/main/contracts/nftItem_gameAsset.tact


  ```
  
receive(msg: Mint){
    self.requireOwner();
    self.mint(sender(), msg.price);
  }

  fun mint(receiver: Address, price: Int) {
    require(self.next_item_index >= 0, "items are not in sequal!");
    let nft_init: StateInit = self.getNftItemInit(self.next_item_index, price);
    let msgValue: Int = context().value;
    let tonBalanceBeforeMsg: Int = (myBalance() - msgValue);
    let storageFee: Int =
      (self.minTonForStorage - min(tonBalanceBeforeMsg, self.minTonForStorage));
    msgValue = (msgValue - (storageFee + self.gasConsumption));
    send(SendParameters{
        to: contractAddress(nft_init),
        value: msgValue,
        mode: SendIgnoreErrors,
        bounce: false,
        body: Transfer{query_id: 0, new_owner: receiver}.toCell(),
        code: nft_init.code,
        data: nft_init.data
      }
    );
    self.itemRecord.set(self.next_item_index, contractAddress(nft_init));
    self.next_item_index = (self.next_item_index + 1);
  }


  ```

## Deployed Contracts Address:

* NFT Collection : https://testnet.tonscan.org/address/EQDzbQTEbzQ-tEeXTrXO0_DKl95T1XvduhNwvsHsDCeLlV-T

* FunPass : https://testnet.tonscan.org/address/EQALJcLY4W_2arhetVVz6IQr9EGjDlKbeLYk79PXdI5VGXtO

* GameAsset :https://testnet.explorer.tonnft.tools/collection/kQCGIRlss8n7ovMDedH_RyMzp8gQ7DcUxHvhaDQ_A2zmjbVT


# It includes

**FunFeed**

<img width="485" alt="1" src="https://github.com/Disha1998/SFS-TON-Readme/assets/69969675/650e45de-29a0-462f-b43c-cb37894cb871">


**Create Feed**

<img width="483" alt="2" src="https://github.com/Disha1998/SFS-TON-Readme/assets/69969675/2f6ea252-442a-493c-b674-d61fbeb23cee">


**Send a Reward**

<img width="479" alt="4" src="https://github.com/Disha1998/SFS-TON-Readme/assets/69969675/ff6e0090-c876-4a57-9956-2ade8eaabbbf">


**Buy FunPass**

<img width="479" alt="4" src="https://github.com/Disha1998/SFS-TON-Readme/assets/69969675/e6aa989c-582f-467e-9505-bdfe51861252">


**Token Smash Game**

<img width="482" alt="5" src="https://github.com/Disha1998/SFS-TON-Readme/assets/69969675/4b43c6bb-8df2-4028-88b7-e4ccb9125558">

![5(1)](https://github.com/Disha1998/SFS-TON-Readme/assets/69969675/865217e5-25b7-4b88-948d-8b2722b26866)

![5(2)](https://github.com/Disha1998/SFS-TON-Readme/assets/69969675/b845ac2a-8c74-4ab9-ab24-d1d868443c46)

![5(3)](https://github.com/Disha1998/SFS-TON-Readme/assets/69969675/2f5abc6c-cc1e-4aec-aeb1-d7e01712f9b0)

![5(4)](https://github.com/Disha1998/SFS-TON-Readme/assets/69969675/dc193aa8-f510-4861-b200-d00a9779431f)




**LeaderBoard** 

<img width="479" alt="6" src="https://github.com/Disha1998/SFS-TON-Readme/assets/69969675/eadecc3a-6118-4ca8-aadf-8f9d51ca6ae1">


 # Let's Connect!
[SuperFunSocial](https://x.com/SuperFunSocial "Visit SFS's Profile")
[Karan Pujara](https://x.com/karan_pujara "Visit Karan's Profile")
[Dhruv Sathavara](https://x.com/Dhruv_Slat "Visit Dhruv's Profile")
[Nirav Joshi](https://x.com/NiravJ3 "Visit Nirav's Profile")
[Disha Sathavara](https://x.com/dishasathavara "Visit Disha's Profile")
[Mahima Thacker](https://x.com/mahima_thacker "Visit Mahima's Profile")


