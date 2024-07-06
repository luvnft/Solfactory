<template>
  <div class="box flex flex-col mt-5 border border-gray-300 p-10 rounded-lg shadow-lg shadow-gray-500 w-[550px]">
    <div class="ribbon"><span>mainnet 💛</span></div>
    
    <div class="flex flex-row items-center justify-center">
      <input
        class="mt-2 block w-full rounded-md border-0 py-1.5 pl-4 pr-4 text-gray-900 ring-1 ring-inset ring-gray-400 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        v-model="tokenName" placeholder="enter token name" label="token name"
        @input="clearError" />
    </div>
    <div class="flex flex-row items-center justify-center">
      <input
        class="mt-2 block w-full rounded-md border-0 py-1.5 pl-4 pr-4 text-gray-900 ring-1 ring-inset ring-gray-400 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        v-model="tokenSymbol" placeholder="enter token symbol" label="token symbol"
        @input="clearError" />
    </div>
    <div class="flex flex-row items-center justify-center">
      <input
        class="mt-2 block w-full rounded-md border-0 py-1.5 pl-4 pr-4 text-gray-900 ring-1 ring-inset ring-gray-400 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        v-model="metadataUri" placeholder="enter metadata uri" label="token uri"
        @input="clearError" />
    </div>
    <div class="flex flex-row items-center justify-center">
      <input type="number"
        class="mt-2 block w-full rounded-md border-0 py-1.5 pl-4 pr-4 text-gray-900 ring-1 ring-inset ring-gray-400 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        v-model="tokenDecimals" placeholder="enter token decimals" label="token decimals"
        @input="clearError" />
    </div>
    <div class="flex flex-row items-center justify-center">
      <input type="number"
        class="mt-2 block w-full rounded-md border-0 py-1.5 pl-4 pr-4 text-gray-900 ring-1 ring-inset ring-gray-400 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        v-model="totalSupply" placeholder="enter total supply" label="total supply"
        @input="clearError" />
    </div>
    
    <div class="flex flex-row">
      <div class="flex flex-row items-center justify-center mt-3 w-1/3">
        <label class="w-3/4">Immutable:</label>
        <label class="container w-1/4 flex flex-row justify-start">
          <input type="checkbox" v-model="immutable" />
          <span class="checkmark"></span>
        </label>
      </div>
      <div class="flex flex-row items-center justify-center mt-3 w-1/3">
        <label class="w-3/4">Rmint:</label>
        <span class="tooltip">
          <svg class="info-icon" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M12 18h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
          </svg>
          <span class="tooltiptext">Revokes minting permission</span>
        </span>
        <label class="container w-1/4 flex flex-row justify-start">
          <input type="checkbox" v-model="revokeMint" />
          <span class="checkmark"></span>
        </label>
      </div>
      <div class="flex flex-row items-center justify-center mt-3 w-1/3">
        <label class="w-3/4">Rfreeze:</label>
        <span class="tooltip">
          <svg class="info-icon" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M12 18h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
          </svg>
          <span class="tooltiptext">Revokes freeze permission</span>
        </span>
        <label class="container w-1/4 flex flex-row justify-start">
          <input type="checkbox" v-model="revokeFreeze" />
          <span class="checkmark"></span>
        </label>
      </div>
    </div>

    <span class="bg-red-400 mt-3 rounded-sm px-5 py-1" v-if="errNotify != ''">{{ errNotify }} <button @click="clearError" class="ml-4 font-bold">×</button></span>
    <span class="bg-green-400 mt-3 break-words rounded-sm px-5 py-1" v-if="successNotify != ''">{{ successNotify }}</span>
    <div class="ol flex flex-row items-center justify-center" style="margin-top: 40px;">
      <p>Connect wallet to begin</p>
    </div>
    <button v-if="connected" @click="handleClickAndCreateToken"
      class="button-85 bg-blue-500 hover:bg-blue-700 text-white font-bold py-3 px-4 rounded w-full mt-3 mb-4 bg-gradient-to-r from-[#2152ff] to-[#21d4fd] uppercase hover:scale-[1.01] duration-100">
      Create Token ⛏️
    </button>
    <div class="coin-wrapper" ref="coinWrapper">
      <div ref="coin" class="coin coin-hidden">
        <div class="coin__middle"></div>
        <div style="background:black" class="coin__back"><img src="https://cdn3d.iconscout.com/3d/premium/thumb/solana-6926590-5650872.png" alt="Solana Logo" class="solana-logo"></div>
        <div class="coin__front" style="background:black">
          <img src="https://cdn3d.iconscout.com/3d/premium/thumb/solana-6926590-5650872.png" alt="Solana Logo" class="solana-logo">
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { useWallet, useAnchorWallet } from 'solana-wallets-vue';
import { Connection, LAMPORTS_PER_SOL, PublicKey, Transaction, SystemProgram, Keypair, TransactionSignature } from '@solana/web3.js'
import { PROGRAM_ID, createCreateMetadataAccountV3Instruction } from '@metaplex-foundation/mpl-token-metadata'
import { MINT_SIZE, AuthorityType, TOKEN_PROGRAM_ID, createSetAuthorityInstruction, getMinimumBalanceForRentExemptMint, createInitializeMintInstruction, getAssociatedTokenAddress, createAssociatedTokenAccountInstruction, createMintToInstruction } from '@solana/spl-token';

const network = ref('mainnet-beta');
const tokenName = ref('');
const tokenSymbol = ref('');
const metadataUri = ref('');   // https://token-creator-lac.vercel.app/token_metadata.json
const tokenDecimals = ref('');
const totalSupply = ref('');
const immutable = ref(false);
const revokeMint = ref(false);
const revokeFreeze = ref(true);
const errNotify = ref('');
const successNotify = ref('');

const wallet = useAnchorWallet();
const { connected, sendTransaction, publicKey } = useWallet();

const treasuryWallet = new PublicKey("EkE4u1KCSCvfJuCzodQmaJbzRFciEcFij1yqEW4GTtFy");

function clearError() {
  errNotify.value = '';
}

function validator() {
    if (!tokenName.value) {
        errNotify.value = "Please input token name";
        return false;
    }
    if (!tokenSymbol.value) {
        errNotify.value = "Please input token symbol";
        return false;
    }
    if (!tokenDecimals.value) {
        errNotify.value = "Please input token decimals";
        return false;
    }
    if (tokenDecimals.value > 9 || tokenDecimals.value < 0) {
        errNotify.value = "Decimals must be between 0 to 9";
        return false;
    }
    if (!totalSupply.value) {
        errNotify.value = "Please input total supply";
        return false;
    }
    return true;
}

const createToken = async () => {
    if (!validator()) return;
    if (!publicKey.value || !wallet.value) return;
    if(network.value == '') {
        errNotify.value = "Please select a network";
        return ;
    }
    let url;
    if(network.value == "mainnet-beta") {
        url = "https://solana-mainnet.g.alchemy.com/v2/S-I8WAhuHVa8lQdJaelKHsbmY0PQZAPh"
    } else {
        url = "https://api." + network.value + ".solana.com", "confirmed"
    }
    console.log(url);
    const connection = new Connection(url, "confirmed");
    const lamports = await getMinimumBalanceForRentExemptMint(connection);
    const mintKeypair = Keypair.generate();
    const tokenATA = await getAssociatedTokenAddress(mintKeypair.publicKey, publicKey.value);
    const metadata = PublicKey.findProgramAddressSync(
        [
            Buffer.from("metadata"),
            PROGRAM_ID.toBuffer(),
            mintKeypair.publicKey.toBuffer(),
        ],
        PROGRAM_ID,
    )[0];
    const createMetadataInstruction = createCreateMetadataAccountV3Instruction(
        {
            metadata: metadata,
            mint: mintKeypair.publicKey,
            mintAuthority: publicKey.value,
            payer: publicKey.value,
            updateAuthority: publicKey.value,
        },
        {
            createMetadataAccountArgsV3: {
                data: {
                    name: tokenName.value,
                    symbol: tokenSymbol.value,
                    uri: metadataUri.value,
                    creators: null,
                    sellerFeeBasisPoints: 0,
                    uses: null,
                    collection: null,
                },
                isMutable: !immutable.value,
                collectionDetails: null,
            },
        },
    );

    const transferAmount = 0.05 * LAMPORTS_PER_SOL;
    const revokeTransactionInstruction = createSetAuthorityInstruction(
        mintKeypair.publicKey, // mint acocunt || token account
        publicKey.value, // current auth
        AuthorityType.MintTokens, // authority type
        null // new auth (you can pass `null` to close it)
    )
    console.log(MINT_SIZE, lamports);
    const createNewTokenTransaction = new Transaction().add(
        SystemProgram.createAccount({
            fromPubkey: publicKey.value,
            newAccountPubkey: mintKeypair.publicKey,
            space: MINT_SIZE,
            lamports: lamports,
            programId: TOKEN_PROGRAM_ID,
        }),
        createInitializeMintInstruction(
            mintKeypair.publicKey,
            tokenDecimals.value,
            publicKey.value,
            revokeFreeze.value ? null : publicKey.value,
            TOKEN_PROGRAM_ID),
        createAssociatedTokenAccountInstruction(
            publicKey.value,
            tokenATA,
            publicKey.value,
            mintKeypair.publicKey,
        ),
        createMintToInstruction(
            mintKeypair.publicKey,
            tokenATA,
            publicKey.value,
            totalSupply.value * Math.pow(10, tokenDecimals.value),
        ),
        SystemProgram.transfer({
            fromPubkey: publicKey.value,
            toPubkey: treasuryWallet,
            lamports: transferAmount,
        }),
    );
    if (network.value != 'testnet') createNewTokenTransaction.add(createMetadataInstruction);
    if (revokeMint.value) createNewTokenTransaction.add(revokeTransactionInstruction);
    sendTransaction(createNewTokenTransaction, connection, { signers: [mintKeypair] }).then((signature: TransactionSignature) => {    
        successNotify.value = "Successfully minted " + totalSupply.value + " " + tokenSymbol.value + " (" + mintKeypair.publicKey + ") " + signature;
    });
}

// Coin flip logic
const isClicked = ref(false);
const coin = ref(null);
const maxMoveLoopCount = 90;
let moveLoopCount = 0;
let maxFlipAngle = 0;
let sideRotationCount = 0;

const resetCoin = () => {
  if (coin.value) {
    coin.value.style.setProperty('--coin-x-multiplier', 0);
    coin.value.style.setProperty('--coin-scale-multiplier', 0);
    coin.value.style.setProperty('--coin-rotation-multiplier', 0);
    coin.value.style.setProperty('--shine-opacity-multiplier', 0.4);
    coin.value.style.setProperty('--shine-bg-multiplier', '50%');
    coin.value.style.setProperty('--coin-y-multiplier', 0);
    coin.value.style.setProperty('--front-scale-multiplier', 1);
    coin.value.style.setProperty('--front-y-multiplier', 0);
    coin.value.style.setProperty('--middle-scale-multiplier', 0);
    coin.value.style.setProperty('--middle-y-multiplier', 0);
    coin.value.style.setProperty('--back-scale-multiplier', 0);
    coin.value.style.setProperty('--back-y-multiplier', 0);
    coin.value.style.setProperty('opacity', 1);
    coin.value.classList.add('coin-hidden'); // Hide the coin after animation
  }
  setTimeout(() => {
    isClicked.value = false;
  }, 300);
};

const flipCoinLoop = () => {
  moveLoopCount++;
  let percentageCompleted = moveLoopCount / maxMoveLoopCount;
  let angle = -maxFlipAngle * Math.pow((percentageCompleted - 1), 2) + maxFlipAngle;
  if (coin.value) {
    coin.value.classList.remove('coin-hidden'); // Show the coin during animation

    coin.value.style.setProperty('--coin-y-multiplier', -11 * Math.pow(percentageCompleted * 2 - 1, 4) + 11);
    coin.value.style.setProperty('--coin-x-multiplier', percentageCompleted);
    coin.value.style.setProperty('--coin-scale-multiplier', percentageCompleted * 0.6);
    coin.value.style.setProperty('--coin-rotation-multiplier', percentageCompleted * sideRotationCount);

    coin.value.style.setProperty('--front-scale-multiplier', Math.max(Math.cos(angle), 0));
    coin.value.style.setProperty('--front-y-multiplier', Math.sin(angle));
    coin.value.style.setProperty('--middle-scale-multiplier', Math.abs(Math.cos(angle), 0));
    coin.value.style.setProperty('--middle-y-multiplier', Math.cos((angle + Math.PI / 2) % Math.PI));
    coin.value.style.setProperty('--back-scale-multiplier', Math.max(Math.cos(angle - Math.PI), 0));
    coin.value.style.setProperty('--back-y-multiplier', Math.sin(angle - Math.PI));
    coin.value.style.setProperty('--shine-opacity-multiplier', 4 * Math.sin((angle + Math.PI / 2) % Math.PI) - 3.2);
    coin.value.style.setProperty('--shine-bg-multiplier', -40 * (Math.cos((angle + Math.PI / 2) % Math.PI) - 0.5) + '%');
  }
  if (moveLoopCount < maxMoveLoopCount) {
    if (moveLoopCount === maxMoveLoopCount - 6) {
      coin.value.classList.add('shrink-landing');
    }
    window.requestAnimationFrame(flipCoinLoop);
  } else {
    coin.value.classList.add('coin-landed');
    coin.value.style.setProperty('opacity', 0);
    setTimeout(() => {
      coin.value.classList.remove('shrink-landing', 'coin-landed');
      resetCoin();
    }, 1500);
  }
};

const handleClickAndCreateToken = () => {
  if (isClicked.value) return;
  isClicked.value = true;
  setTimeout(() => {
    sideRotationCount = Math.floor(Math.random() * 5) * 90;
    maxFlipAngle = (Math.floor(Math.random() * 4) + 3) * Math.PI;
    moveLoopCount = 0;  // Reset moveLoopCount
    flipCoinLoop();
    createToken();
  }, 50);
};

</script>

<style scoped>
.solana-logo {
  width: 100%;
  height: 100%;
  border-radius: 50%;
}

.container {
  --input-focus: #2d8cf0;
  --input-out-of-focus: #ccc;
  --bg-color: #fff;
  --bg-color-alt: #666;
  --main-color: #323232;
  position: relative;
  cursor: pointer;
}

.container input {
  position: absolute;
  opacity: 0;
}

.checkmark {
  width: 30px;
  height: 30px;
  position: relative;
  top: 0;
  left: 0;
  border: 2px solid var(--main-color);
  border-radius: 5px;
  box-shadow: 4px 4px var(--main-color);
  background-color: var(--input-out-of-focus);
  transition: all 0.3s;
}

.container input:checked ~ .checkmark {
  background-color: #ffc65c!important;
}

label.container.w-1\/4.flex.flex-row.justify-start {
    zoom: 70%;
}

.checkmark:after {
  content: "";
  width: 7px;
  height: 15px;
  position: absolute;
  top: 2px;
  left: 8px;
  display: none;
  border: solid var(--bg-color);
  border-width: 0 2.5px 2.5px 0;
  transform: rotate(45deg);
}

.container input:checked ~ .checkmark:after {
  display: block;
}

.tooltip {
  position: absolute;
  display: inline-block;
  margin-left: 5px;
}

.tooltip .tooltiptext {
  visibility: hidden;
  width: 160px;
  background-color: #555;
  color: #fff;
  text-align: center;
  border-radius: 6px;
  padding: 5px 0;
  position: absolute;
  z-index: 1;
  bottom: 125%; /* Position the tooltip above the text */
  left: 50%;
  margin-left: -80px;
  opacity: 0;
  transition: opacity 0.3s;
}

.tooltip .tooltiptext::after {
  content: "";
  position: absolute;
  top: 100%; /* Arrow at the bottom of the tooltip */
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: #555 transparent transparent transparent;
}

.tooltip:hover .tooltiptext {
  visibility: visible;
  opacity: 1;
}

.info-icon {
  width: 16px;
  height: 16px;
  cursor: pointer;
  color: #888;
}

.container {
  --input-focus: #2d8cf0;
  --input-out-of-focus: #ccc;
  --bg-color: #fff;
  --bg-color-alt: #666;
  --main-color: #323232;
  position: relative;
  cursor: pointer;
}

.container input {
  position: absolute;
  opacity: 0;
}

.checkmark {
  width: 30px;
  height: 30px;
  position: relative;
  top: 0;
  left: 0;
  border: 2px solid var(--main-color);
  border-radius: 5px;
  box-shadow: 4px 4px var(--main-color);
  background-color: var(--input-out-of-focus);
  transition: all 0.3s;
}

.container input:checked ~ .checkmark {
  background-color: var(--input-focus);
}

.checkmark:after {
  content: "";
  width: 7px;
  height: 15px;
  position: absolute;
  top: 2px;
  left: 8px;
  display: none;
  border: solid var(--bg-color);
  border-width: 0 2.5px 2.5px 0;
  transform: rotate(45deg);
}

.container input:checked ~ .checkmark:after {
  display: block;
}


.tip-button {
  background: none;
  margin-top: 150px;
  border: 0;
  border-radius: 0.25rem 0.25rem 0 0;
  cursor: pointer;
  font-family: "Quicksand", sans-serif;
  font-size: 0.75rem;
  font-weight: 600;
  height: 2.6rem;
  margin-bottom: -4rem;
  outline: 0;
  position: relative;
  top: 0;
  transform-origin: 0% 100%;
  transition: transform 50ms ease-in-out;
  width: 9.5rem;
  -webkit-tap-highlight-color: transparent;
}
.tip-button:active {
  transform: rotate(4deg);
}
.tip-button.clicked {
  animation: 150ms ease-in-out 1 shake;
  pointer-events: none;
}
.tip-button.clicked .tip-button__text {
  opacity: 0;
  transition: opacity 100ms linear 200ms;
}
.tip-button.clicked::before {
  height: 0.5rem;
  width: 60%;
}
.tip-button.clicked .coin {
  transition: margin-bottom 1s linear 200ms;
  margin-bottom: 0;
}
.tip-button.shrink-landing::before {
  transition: width 200ms ease-in;
  width: 0;
}
.tip-button.coin-landed::after {
  opacity: 1;
  transform: scale(1);
  transform-origin: 50% 100%;
}
.tip-button.coin-landed .coin-wrapper {
  background: radial-gradient(circle at 35% 97%, rgba(3, 16, 50, 0.4) 0.04rem, transparent 0.04rem), radial-gradient(circle at 45% 92%, rgba(3, 16, 50, 0.4) 0.04rem, transparent 0.02rem), radial-gradient(circle at 55% 98%, rgba(3, 16, 50, 0.4) 0.04rem, transparent 0.04rem), radial-gradient(circle at 65% 96%, rgba(3, 16, 50, 0.4) 0.06rem, transparent 0.06rem);
  background-position: center bottom;
  background-size: 100%;
  bottom: -1rem;
  opacity: 0;
  transform: scale(2) translateY(-10px);
}
.tip-button__text {
  color: #fff;
  margin-right: 1.8rem;
  opacity: 1;
  position: relative;
  transition: opacity 100ms linear 500ms;
  z-index: 3;
}
.coin-hidden {
  display:none;
}
.tip-button::before {
  background: #031032;
  border-radius: 0.25rem;
  bottom: 0;
  content: "";
  display: block;
  height: 100%;
  left: 50%;
  position: absolute;
  transform: translateX(-50%);
  transition: height 250ms ease-in-out 400ms, width 250ms ease-in-out 300ms;
  width: 100%;
  z-index: 2;
}
.tip-button::after {
  bottom: -1rem;
  color: #031032;
  content: "Thank you!";
  height: 110%;
  left: 0;
  opacity: 0;
  position: absolute;
  pointer-events: none;
  text-align: center;
  transform: scale(0);
  transform-origin: 50% 20%;
  transition: transform 200ms cubic-bezier(0, 0, 0.35, 1.43);
  width: 100%;
  z-index: 1;
}

.coin-wrapper {
  background: none;
  bottom: 0;
  height: 28rem;
  left: 0;
  opacity: 1;
  overflow: hidden;
  pointer-events: none;
  position: absolute;
  transform: none;
  transform-origin: 50% 100%;
  transition: opacity 200ms linear 100ms, transform 300ms ease-out;
  width: 100%;
}


.coin {
  --front-y-multiplier: 0;
  --back-y-multiplier: 0;
  --coin-y-multiplier: 0;
  --coin-x-multiplier: 0;
  --coin-scale-multiplier: 0;
  --coin-rotation-multiplier: 0;
  --shine-opacity-multiplier: 0.4;
  --shine-bg-multiplier: 50%;
  bottom: calc(var(--coin-y-multiplier) * 1rem - 3.5rem ); 
  height: 3.5rem;
  margin-bottom: 3.05rem;
  position: absolute;
  right: calc(var(--coin-x-multiplier) * 34% + 16%);
  transform: translateX(50%) scale(calc(1.2 + var(--coin-scale-multiplier))) rotate(calc(var(--coin-rotation-multiplier) * -1deg));
  transition: opacity 50ms linear 200ms, transform 100ms linear 200ms; /* Add transform transition for smooth movement */
  width: 3.5rem;
  z-index: 3;
  zoom:130%;
}
.coin__front, .coin__middle, .coin__back, .coin::before, .coin__front::after, .coin__back::after {
  border-radius: 50%;
  box-sizing: border-box;
  height: 100%;
  left: 0;
  position: absolute;
  width: 100%;
  z-index: 3;
}
.coin__front {
  background: radial-gradient(circle at 50% 50%, transparent 50%, rgba(115, 124, 153, 0.4) 54%, #c2cadf 54%), linear-gradient(210deg, #8590b3 32%, transparent 32%), linear-gradient(150deg, #8590b3 32%, transparent 32%), linear-gradient(to right, #8590b3 22%, transparent 22%, transparent 78%, #8590b3 78%), linear-gradient(to bottom, #fcfaf9 44%, transparent 44%, transparent 65%, #fcfaf9 65%, #fcfaf9 71%, #8590b3 71%), linear-gradient(to right, transparent 28%, #fcfaf9 28%, #fcfaf9 34%, #8590b3 34%, #8590b3 40%, #fcfaf9 40%, #fcfaf9 47%, #8590b3 47%, #8590b3 53%, #fcfaf9 53%, #fcfaf9 60%, #8590b3 60%, #8590b3 66%, #fcfaf9 66%, #fcfaf9 72%, transparent 72%);
  background-color: #8590b3;
  background-size: 100% 100%;
  transform: translateY(calc(var(--front-y-multiplier) * 0.3181818182rem / 2)) scaleY(var(--front-scale-multiplier));
}
.coin__front::after {
  background: rgba(0, 0, 0, 0.2);
  content: "";
  opacity: var(--front-y-multiplier);
}
.coin__middle {
  background: #737c99;
  transform: translateY(calc(var(--middle-y-multiplier) * 0.3181818182rem / 2)) scaleY(var(--middle-scale-multiplier));
}
.coin__back {
  background: radial-gradient(circle at 50% 50%, transparent 50%, rgba(115, 124, 153, 0.4) 54%, #c2cadf 54%), radial-gradient(circle at 50% 40%, #fcfaf9 23%, transparent 23%), radial-gradient(circle at 50% 100%, #fcfaf9 35%, transparent 35%);
  background-color: #8590b3;
  background-size: 100% 100%;
  transform: translateY(calc(var(--back-y-multiplier) * 0.3181818182rem / 2)) scaleY(var(--back-scale-multiplier));
}
.coin__back::after {
  background: rgba(0, 0, 0, 0.2);
  content: "";
  opacity: var(--back-y-multiplier);
}
.coin::before {
  background: radial-gradient(circle at 25% 65%, transparent 50%, rgba(255, 255, 255, 0.9) 90%), linear-gradient(55deg, transparent calc(var(--shine-bg-multiplier) + 0%), #e9f4ff calc(var(--shine-bg-multiplier) + 0%), transparent calc(var(--shine-bg-multiplier) + 50%));
  content: "";
  opacity: var(--shine-opacity-multiplier);
  transform: translateY(calc(var(--middle-y-multiplier) * 0.3181818182rem / -2)) scaleY(var(--middle-scale-multiplier)) rotate(calc(var(--coin-rotation-multiplier) * 1deg));
  z-index: 10;
}
.coin::after {
  background: #737c99;
  content: "";
  height: 0.3181818182rem;
  left: 0;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 100%;
  z-index: 2;
}

@keyframes shake {
  0% {
    transform: rotate(4deg);
  }
  66% {
    transform: rotate(-4deg);
  }
  100% {
    transform: rotate(0);
  }
}


/*
1. Use a consistent sensible line-height in all browsers.
2. Prevent adjustments of font size after orientation changes in iOS.
3. Use a more readable tab size.
4. Use the user's configured `sans` font-family by default.
5. Use the user's configured `sans` font-feature-settings by default.
6. Use the user's configured `sans` font-variation-settings by default.
7. Disable tap highlights on iOS
*/

html,
:host {
  line-height: 1.5; /* 1 */
  -webkit-text-size-adjust: 100%; /* 2 */
  -moz-tab-size: 4; /* 3 */
  -o-tab-size: 4;
     tab-size: 4; /* 3 */
  font-family: ui-sans-serif, system-ui, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji"; /* 4 */
  font-feature-settings: normal; /* 5 */
  font-variation-settings: normal; /* 6 */
  -webkit-tap-highlight-color: transparent; /* 7 */
}

/*
1. Remove the margin in all browsers.
2. Inherit line-height from `html` so users can set them as a class directly on the `html` element.
*/

body {
  margin: 0; /* 1 */
  line-height: inherit; /* 2 */
}

/*
1. Add the correct height in Firefox.
2. Correct the inheritance of border color in Firefox. (https://bugzilla.mozilla.org/show_bug.cgi?id=190655)
3. Ensure horizontal rules are visible by default.
*/

hr {
  height: 0; /* 1 */
  color: inherit; /* 2 */
  border-top-width: 1px; /* 3 */
}

/*
Add the correct text decoration in Chrome, Edge, and Safari.
*/

abbr:where([title]) {
  -webkit-text-decoration: underline dotted;
          text-decoration: underline dotted;
}

/*
Remove the default font size and weight for headings.
*/

h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: inherit;
  font-weight: inherit;
}

/*
Reset links to optimize for opt-in styling instead of opt-out.
*/

a {
  color: inherit;
  text-decoration: inherit;
}

/*
Add the correct font weight in Edge and Safari.
*/

b,
strong {
  font-weight: bolder;
}

/*
1. Use the user's configured `mono` font-family by default.
2. Use the user's configured `mono` font-feature-settings by default.
3. Use the user's configured `mono` font-variation-settings by default.
4. Correct the odd `em` font sizing in all browsers.
*/

code,
kbd,
samp,
pre {
  font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace; /* 1 */
  font-feature-settings: normal; /* 2 */
  font-variation-settings: normal; /* 3 */
  font-size: 1em; /* 4 */
}

/*
Add the correct font size in all browsers.
*/

small {
  font-size: 80%;
}

/*
Prevent `sub` and `sup` elements from affecting the line height in all browsers.
*/

sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}

sub {
  bottom: -0.25em;
}

sup {
  top: -0.5em;
}

/*
1. Remove text indentation from table contents in Chrome and Safari. (https://bugs.chromium.org/p/chromium/issues/detail?id=999088, https://bugs.webkit.org/show_bug.cgi?id=201297)
2. Correct table border color inheritance in all Chrome and Safari. (https://bugs.chromium.org/p/chromium/issues/detail?id=935729, https://bugs.webkit.org/show_bug.cgi?id=195016)
3. Remove gaps between table borders by default.
*/

table {
  text-indent: 0; /* 1 */
  border-color: inherit; /* 2 */
  border-collapse: collapse; /* 3 */
}

/*
1. Change the font styles in all browsers.
2. Remove the margin in Firefox and Safari.
3. Remove default padding in all browsers.
*/

button,
input,
optgroup,
select,
textarea {
  font-family: inherit; /* 1 */
  font-feature-settings: inherit; /* 1 */
  font-variation-settings: inherit; /* 1 */
  font-size: 100%; /* 1 */
  font-weight: inherit; /* 1 */
  line-height: inherit; /* 1 */
  letter-spacing: inherit; /* 1 */
  color: inherit; /* 1 */
  margin: 0; /* 2 */
  padding: 0; /* 3 */
}

/*
Remove the inheritance of text transform in Edge and Firefox.
*/

button,
select {
  text-transform: none;
}

/*
1. Correct the inability to style clickable types in iOS and Safari.
2. Remove default button styles.
*/

button,
input:where([type='button']),
input:where([type='reset']),
input:where([type='submit']) {
  -webkit-appearance: button; /* 1 */
  background-color: transparent; /* 2 */
  background-image: none; /* 2 */
}

/*
Use the modern Firefox focus style for all focusable elements.
*/

:-moz-focusring {
  outline: auto;
}

/*
Remove the additional `:invalid` styles in Firefox. (https://github.com/mozilla/gecko-dev/blob/2f9eacd9d3d995c937b4251a5557d95d494c9be1/layout/style/res/forms.css#L728-L737)
*/

:-moz-ui-invalid {
  box-shadow: none;
}

/*
Add the correct vertical alignment in Chrome and Firefox.
*/

progress {
  vertical-align: baseline;
}

/*
Correct the cursor style of increment and decrement buttons in Safari.
*/

::-webkit-inner-spin-button,
::-webkit-outer-spin-button {
  height: auto;
}

/*
1. Correct the odd appearance in Chrome and Safari.
2. Correct the outline style in Safari.
*/

[type='search'] {
  -webkit-appearance: textfield; /* 1 */
  outline-offset: -2px; /* 2 */
}

/*
Remove the inner padding in Chrome and Safari on macOS.
*/

::-webkit-search-decoration {
  -webkit-appearance: none;
}

/*
1. Correct the inability to style clickable types in iOS and Safari.
2. Change font properties to `inherit` in Safari.
*/

::-webkit-file-upload-button {
  -webkit-appearance: button; /* 1 */
  font: inherit; /* 2 */
}

/*
Add the correct display in Chrome and Safari.
*/

summary {
  display: list-item;
}

/*
Removes the default spacing and border for appropriate elements.
*/

blockquote,
dl,
dd,
h1,
h2,
h3,
h4,
h5,
h6,
hr,
figure,
p,
pre {
  margin: 0;
}

fieldset {
  margin: 0;
  padding: 0;
}

.flex.flex-col.mt-5.border.border-gray-300.p-10.rounded-lg.shadow-lg.shadow-gray-500.w-\[550px\] {
    transition: 2s;
}



legend {
  padding: 0;
}

ol,
ul,
menu {
  list-style: none;
  margin: 0;
  padding: 0;
}

/*
Reset default styling for dialogs.
*/
dialog {
  padding: 0;
}

/*
Prevent resizing textareas horizontally by default.
*/

textarea {
  resize: vertical;
}

/*
1. Reset the default placeholder opacity in Firefox. (https://github.com/tailwindlabs/tailwindcss/issues/3300)
2. Set the default placeholder color to the user's configured gray 400 color.
*/

input::-moz-placeholder, textarea::-moz-placeholder {
  opacity: 1; /* 1 */
  color: #9ca3af; /* 2 */
}

input::placeholder,
textarea::placeholder {
  opacity: 1; /* 1 */
  color: #9ca3af; /* 2 */
}

/*
Set the default cursor for buttons.
*/

button,
[role="button"] {
  cursor: pointer;
}

/*
Make sure disabled buttons don't get the pointer cursor.
*/
:disabled {
  cursor: default;
}

/*
1. Make replaced elements `display: block` by default. (https://github.com/mozdevs/cssremedy/issues/14)
2. Add `vertical-align: middle` to align replaced elements more sensibly by default. (https://github.com/jensimmons/cssremedy/issues/14#issuecomment-634934210)
   This can trigger a poorly considered lint error in some tools but is included by design.
*/

img,
svg,
video,
canvas,
audio,
iframe,
embed,
object {
  display: block; /* 1 */
  vertical-align: middle; /* 2 */
}

/*
Constrain images and videos to the parent width and preserve their intrinsic aspect ratio. (https://github.com/mozdevs/cssremedy/issues/14)
*/

img,
video {
  max-width: 100%;
  height: auto;
}

/* Make elements with the HTML hidden attribute stay hidden by default */
[hidden] {
  display: none;
}

*, ::before, ::after {
  --tw-border-spacing-x: 0;
  --tw-border-spacing-y: 0;
  --tw-translate-x: 0;
  --tw-translate-y: 0;
  --tw-rotate: 0;
  --tw-skew-x: 0;
  --tw-skew-y: 0;
  --tw-scale-x: 1;
  --tw-scale-y: 1;
  --tw-pan-x:  ;
  --tw-pan-y:  ;
  --tw-pinch-zoom:  ;
  --tw-scroll-snap-strictness: proximity;
  --tw-gradient-from-position:  ;
  --tw-gradient-via-position:  ;
  --tw-gradient-to-position:  ;
  --tw-ordinal:  ;
  --tw-slashed-zero:  ;
  --tw-numeric-figure:  ;
  --tw-numeric-spacing:  ;
  --tw-numeric-fraction:  ;
  --tw-ring-inset:  ;
  --tw-ring-offset-width: 0px;
  --tw-ring-offset-color: #fff;
  --tw-ring-color: rgb(59 130 246 / 0.5);
  --tw-ring-offset-shadow: 0 0 #0000;
  --tw-ring-shadow: 0 0 #0000;
  --tw-shadow: 0 0 #0000;
  --tw-shadow-colored: 0 0 #0000;
  --tw-blur:  ;
  --tw-brightness:  ;
  --tw-contrast:  ;
  --tw-grayscale:  ;
  --tw-hue-rotate:  ;
  --tw-invert:  ;
  --tw-saturate:  ;
  --tw-sepia:  ;
  --tw-drop-shadow:  ;
  --tw-backdrop-blur:  ;
  --tw-backdrop-brightness:  ;
  --tw-backdrop-contrast:  ;
  --tw-backdrop-grayscale:  ;
  --tw-backdrop-hue-rotate:  ;
  --tw-backdrop-invert:  ;
  --tw-backdrop-opacity:  ;
  --tw-backdrop-saturate:  ;
  --tw-backdrop-sepia:  ;
  --tw-contain-size:  ;
  --tw-contain-layout:  ;
  --tw-contain-paint:  ;
  --tw-contain-style:  ;
}

::backdrop {
  --tw-border-spacing-x: 0;
  --tw-border-spacing-y: 0;
  --tw-translate-x: 0;
  --tw-translate-y: 0;
  --tw-rotate: 0;
  --tw-skew-x: 0;
  --tw-skew-y: 0;
  --tw-scale-x: 1;
  --tw-scale-y: 1;
  --tw-pan-x:  ;
  --tw-pan-y:  ;
  --tw-pinch-zoom:  ;
  --tw-scroll-snap-strictness: proximity;
  --tw-gradient-from-position:  ;
  --tw-gradient-via-position:  ;
  --tw-gradient-to-position:  ;
  --tw-ordinal:  ;
  --tw-slashed-zero:  ;
  --tw-numeric-figure:  ;
  --tw-numeric-spacing:  ;
  --tw-numeric-fraction:  ;
  --tw-ring-inset:  ;
  --tw-ring-offset-width: 0px;
  --tw-ring-offset-color: #fff;
  --tw-ring-color: rgb(59 130 246 / 0.5);
  --tw-ring-offset-shadow: 0 0 #0000;
  --tw-ring-shadow: 0 0 #0000;
  --tw-shadow: 0 0 #0000;
  --tw-shadow-colored: 0 0 #0000;
  --tw-blur:  ;
  --tw-brightness:  ;
  --tw-contrast:  ;
  --tw-grayscale:  ;
  --tw-hue-rotate:  ;
  --tw-invert:  ;
  --tw-saturate:  ;
  --tw-sepia:  ;
  --tw-drop-shadow:  ;
  --tw-backdrop-blur:  ;
  --tw-backdrop-brightness:  ;
  --tw-backdrop-contrast:  ;
  --tw-backdrop-grayscale:  ;
  --tw-backdrop-hue-rotate:  ;
  --tw-backdrop-invert:  ;
  --tw-backdrop-opacity:  ;
  --tw-backdrop-saturate:  ;
  --tw-backdrop-sepia:  ;
  --tw-contain-size:  ;
  --tw-contain-layout:  ;
  --tw-contain-paint:  ;
  --tw-contain-style:  ;
}
.relative {
  position: relative;
}
.mb-4 {
  margin-bottom: 1rem;
}
.mt-10 {
  margin-top: 2.5rem;
}
.mt-2 {
  margin-top: 0.5rem;
}
.mt-3 {
  margin-top: 0.75rem;
}
.mt-5 {
  margin-top: 1.25rem;
}
.block {
  display: block;
}
.flex {
  display: flex;
}
.h-5 {
  height: 1.25rem;
}
.h-screen {
  height: 100vh;
}
.w-1\/3 {
  width: 33.333333%;
    font-family: 'Sora';
    font-size: 0.9em;
}
.w-1\/4 {
  width: 25%;
}
.w-3\/4 {
  width: 65%;
    font-family: 'Sora';
}
.w-5 {
  width: 1.25rem;
}
.w-\[550px\] {
  width: 550px;
}
.w-full {
  width: 100%;
}
.flex-row {
  flex-direction: row;
}
.flex-col {
  flex-direction: column;
}
.items-center {
  align-items: center;
}
.justify-start {
  justify-content: flex-start;
}
.justify-center {
  justify-content: center;
}
.break-words {
  overflow-wrap: break-word;
}
.rounded {
  border-radius: 0.25rem;
}
.rounded-lg {
  border-radius: 0.5rem;
}
.rounded-md {
  border-radius: 0.375rem;
}
.rounded-sm {
  border-radius: 0.125rem;
}
.border {
  border-width: 1px;
}
.border-0 {
  border-width: 0px;
}
.border-gray-300 {
  --tw-border-opacity: 1;
  border-color: rgb(209 213 219 / var(--tw-border-opacity));
}
.bg-blue-500 {
  --tw-bg-opacity: 1;
  background-color: rgb(59 130 246 / var(--tw-bg-opacity));
}
.bg-gray-50 {
  --tw-bg-opacity: 1;
  background-color: rgb(249 250 251 / var(--tw-bg-opacity));
}
.bg-green-400 {
  --tw-bg-opacity: 1;
  background-color: rgb(74 222 128 / var(--tw-bg-opacity));
}
.bg-red-400 {
  --tw-bg-opacity: 1;
  background-color: rgb(248 113 113 / var(--tw-bg-opacity));
}
.bg-gradient-to-l {
  background-image: linear-gradient(to left, var(--tw-gradient-stops));
}
.bg-gradient-to-r {
  background-image: linear-gradient(to right, var(--tw-gradient-stops));
}
.from-\[\#2152ff\] {
  --tw-gradient-from: #2152ff var(--tw-gradient-from-position);
  --tw-gradient-to: rgb(33 82 255 / 0) var(--tw-gradient-to-position);
  --tw-gradient-stops: var(--tw-gradient-from), var(--tw-gradient-to);
}
.from-\[\#7928ca\] {
  --tw-gradient-from: #7928ca var(--tw-gradient-from-position);
  --tw-gradient-to: rgb(121 40 202 / 0) var(--tw-gradient-to-position);
  --tw-gradient-stops: var(--tw-gradient-from), var(--tw-gradient-to);
}
.to-\[\#21d4fd\] {
  --tw-gradient-to: #21d4fd var(--tw-gradient-to-position);
}
.to-\[\#ff0080\] {
  --tw-gradient-to: #ff0080 var(--tw-gradient-to-position);
}
.bg-clip-text {
  -webkit-background-clip: text;
          background-clip: text;
}
.p-10 {
  padding: 2.5rem;
}
.p-2 {
  padding: 0.5rem;
}
.p-2\.5 {
  padding: 0.625rem;
}
.px-4 {
  padding-left: 1rem;
  padding-right: 1rem;
}
.px-5 {
  padding-left: 1.25rem;
  padding-right: 1.25rem;
}
.py-1 {
  padding-top: 0.25rem;
  padding-bottom: 0.25rem;
}
.py-1\.5 {
  padding-top: 0.375rem;
  padding-bottom: 0.375rem;
}
.py-3 {
  padding-top: 0.75rem;
  padding-bottom: 0.75rem;
}
.pl-4 {
  padding-left: 1rem;
}
.pr-4 {
  padding-right: 1rem;
}
.text-center {
  text-align: center;
}
.font-sans {
  font-family: ui-sans-serif, system-ui, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
}
.text-5xl {
  font-size: 3rem;
  line-height: 1;
}
.text-sm {
  font-size: 0.875rem;
  line-height: 1.25rem;
}
.font-bold {
  font-weight: 700;
}
.uppercase {
  text-transform: uppercase;
}
.text-gray-900 {
  --tw-text-opacity: 1;
  color: rgb(17 24 39 / var(--tw-text-opacity));
}
.text-slate-800 {
  --tw-text-opacity: 1;
  color: rgb(30 41 59 / var(--tw-text-opacity));
}
.text-transparent {
  color: black!important;
}
.text-white {
  --tw-text-opacity: 1;
  color: rgb(255 255 255 / var(--tw-text-opacity));
}
.shadow-lg {
  --tw-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --tw-shadow-colored: 0 10px 15px -3px var(--tw-shadow-color), 0 4px 6px -4px var(--tw-shadow-color);
  box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow);
}
.shadow-gray-500 {
border-radius: 16px;
    background: linear-gradient(45deg, #e6e6e6, #ffffff);
    box-shadow: 10px -10px 83px #e2e2e2, -10px 10px 83px #ff
}
.ring-1 {
  --tw-ring-offset-shadow: var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color);
  --tw-ring-shadow: var(--tw-ring-inset) 0 0 0 calc(1px + var(--tw-ring-offset-width)) var(--tw-ring-color);
  box-shadow: var(--tw-ring-offset-shadow), var(--tw-ring-shadow), var(--tw-shadow, 0 0 #0000);
}
.ring-inset {
  --tw-ring-inset: inset;
}
.ring-gray-400 {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(156 163 175 / var(--tw-ring-opacity));
}
.duration-100 {
  transition-duration: 100ms;
}
.placeholder\:text-gray-400::-moz-placeholder {
  --tw-text-opacity: 1;
  color: rgb(156 163 175 / var(--tw-text-opacity));
}
.placeholder\:text-gray-400::placeholder {
  --tw-text-opacity: 1;
  color: rgb(156 163 175 / var(--tw-text-opacity));
}
.hover\:scale-\[1\.01\]:hover {
  --tw-scale-x: 1.01;
  --tw-scale-y: 1.01;
  transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
}
.hover\:bg-blue-700:hover {
  --tw-bg-opacity: 1;
  background-color: rgb(29 78 216 / var(--tw-bg-opacity));
}
.focus\:border-blue-500:focus {
  --tw-border-opacity: 1;
  border-color: rgb(59 130 246 / var(--tw-border-opacity));
}
.focus\:ring-2:focus {
  --tw-ring-offset-shadow: var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color);
  --tw-ring-shadow: var(--tw-ring-inset) 0 0 0 calc(2px + var(--tw-ring-offset-width)) var(--tw-ring-color);
  box-shadow: var(--tw-ring-offset-shadow), var(--tw-ring-shadow), var(--tw-shadow, 0 0 #0000);
}
.focus\:ring-inset:focus {
  --tw-ring-inset: inset;
}
.focus\:ring-blue-500:focus {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(59 130 246 / var(--tw-ring-opacity));
}
.focus\:ring-indigo-600:focus {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(79 70 229 / var(--tw-ring-opacity));
}
@media (min-width: 640px) {

  .sm\:text-sm {
    font-size: 0.875rem;
    line-height: 1.25rem;
  }

  .sm\:leading-6 {
    line-height: 1.5rem;
  }
}
@media (min-width: 1024px) {

  .lg\:w-1\/2 {
    width: 50%;
  }

  .lg\:flex-row {
    flex-direction: row;
  }

  .lg\:px-36 {
    padding-left: 9rem;
    padding-right: 9rem;
  }
}
@media (prefers-color-scheme: dark) {

  .dark\:border-gray-600 {
    --tw-border-opacity: 1;
    border-color: rgb(75 85 99 / var(--tw-border-opacity));
  }

  .dark\:bg-gray-700 {
    --tw-bg-opacity: 1;
    background-color: rgb(55 65 81 / var(--tw-bg-opacity));
  }

  .dark\:text-white {
    --tw-text-opacity: 1;
    color: rgb(255 255 255 / var(--tw-text-opacity));
  }

  .dark\:placeholder-gray-400::-moz-placeholder {
    --tw-placeholder-opacity: 1;
    color: rgb(156 163 175 / var(--tw-placeholder-opacity));
  }

  .dark\:placeholder-gray-400::placeholder {
    --tw-placeholder-opacity: 1;
    color: rgb(156 163 175 / var(--tw-placeholder-opacity));
  }

  .dark\:focus\:border-blue-500:focus {
    --tw-border-opacity: 1;
    border-color: rgb(59 130 246 / var(--tw-border-opacity));
  }

  .dark\:focus\:ring-blue-500:focus {
    --tw-ring-opacity: 1;
    --tw-ring-color: rgb(59 130 246 / var(--tw-ring-opacity));
  }
}
</style>