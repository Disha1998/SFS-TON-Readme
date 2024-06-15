 # SuperFunSocial

<img width="947" alt="Screenshot 2024-06-14 at 11 41 26 AM" src="https://github.com/Disha1998/SFS-TON-Readme/assets/69969675/e3fbae1a-6215-4d2e-a7d7-96bd38172897">


## What problem we are solving?

**We are solving the problem of creators who don't receive real value for their humorous content. They only get "Likes" and "reputation," and have brand deals as their only earning option, while social media platforms capture all the direct monetary value. Funny content can reach millions in no time, but creators get no tangible reward for their humor, creativity, and time investment.**

## Solution
**SuperFunSocial is a social gaming app on Farcaster & Ton where users can earn crypto rewards for creating entertaining content and playing games.**

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

---screen shots


