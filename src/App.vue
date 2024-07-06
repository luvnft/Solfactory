<script setup lang="ts">
import { onMounted } from 'vue';
import CreateTokenForm from "./components/CreateTokenForm.vue";
import Chatbot from './components/Chatbot-1.vue';
import Modal from './components/ModalTest.vue';
import Popup from './components/PopUp.vue';
import "./assets/add.css";
import CustomButton from './components/WalletButton.vue';
import SolPrice from './components/SolPrice.vue';
import Car from './components/CarOu.vue';
import CarouSe from './components/CarouSe.vue'; 
import LoadingScreen from './components/LoadingScreen.vue'; 




import { PhantomWalletAdapter, SolflareWalletAdapter } from '@solana/wallet-adapter-wallets'
import { initWallet, WalletMultiButton } from 'solana-wallets-vue'
import "solana-wallets-vue/styles.css";
import "./assets/add.css";
require('dotenv').config();

const wallets = [
  new PhantomWalletAdapter(),
  new SolflareWalletAdapter(),
]
initWallet({ wallets, autoConnect: true })

onMounted(() => {
  document.title = 'SPL Forge - Solana Token Factory';
});




</script>


<template>

<LoadingScreen />

<div id="app">
    <Modal />
    
    

  </div>


    <Popup />
 




<div class="bk">
  <div class="relative flex flex-col items-center justify-center h-screen lg:px-36 lg:flex-row">
    <div class="flex flex-col items-center justify-center w-full lg:w-1/2">
      <!--ring div starts here-->

<div style="z-index:222;position: absolute;top: 5%;margin-left: 20%;"><input class="closeflag" id="unique-id-for-box-1" type="checkbox"><div class="msgbox" style="
        border: 2px solid black;
    border-radius: 4px;
    padding: 19px;
    background-image: url(https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExcGlxNm1md2diMnkxMXdwazR3cHh5MXA4Y21ncGlwMG9rcjhndzhwbSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xTiTniuHdUjpOlNo1q/giphy.gif);
    background-size: 100%;
    background-color: #00000078;
    color: white;
    background-position: bottom!important;
    
"><label class="closebutton" for="unique-id-for-box-1"> ❌</label> To initiate token creation, ensure your wallet holds SOL for transaction fees.</div></div>


      <div class="mt-10"><div class="glitch-wrapper" style="
    /* font-size: 3rem; */
"> <div class="glitch" data-text="SPL Forge" style="
    font-size: 6rem;
    font-family: ui-sans-serif, system-ui, sans-serif, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;
    font-weight: 900;
">SPL Forge</div> </div><h1 class="tt text-5xl font-sans text-slate-800 font-bold text-center text-transparent bg-clip-text bg-gradient-to-l from-[#7928ca] to-[#ff0080]" style="position:absolute;margin-top:-145px;font-size:5em;font-weight:100;color:#ffffff29 !important;">SPL TOKEN CREATOR</h1><h3 class="text-center"> ONLY CHAIN FEE. FAST. SECURE<br><span></span></h3></div>
      <div class="mt-5">
        <wallet-multi-button />

        <SolPrice />
        <CustomButton />
        
      </div>
    </div>
    
    
    <div class="flex items-center justify-center lg:w-1/2">

    
     <CarouSe />



<div id="google1" class="modaloverlayy">
  <div class="modal" style="padding: 20px;margin-top: 80px;"><a href="#close" class="close">&times;</a>
 <wallet-multi-button />
<CreateTokenForm />
 
  
     
 
      
      </div>
      </div>

      <div id="google2" class="modaloverlay">
  <div class="modal"><a href="#close" class="close">&times;</a>

  test2
      
      </div>
      </div>

      <Car />
    </div>
    <Chatbot />
</div>


</div>




</template>





    









































<style>

button.swv-button.swv-button-trigger {
    margin-left: auto;
    margin-right: auto;
    
}

a.cr, a.cy {
    padding: 50px;
    border-radius: 23px;
    width: 50%;
    color: #fff;
    padding-left: 20px;
    filter: drop-shadow(2px 4px 6px black);
    height: 1em;
    transition: 2s;
}

p.cto {
    
}

p.cto {
    font-size: 200%;
    transition:1s;

  
}

p.cto:hover {
    font-size: 220%;
  transition:1s;
}

a.cr, a.cy:hover {
    
}


a.cr {
    background: #4A59E0;
    padding: 50px;
    border-radius: 23px;
    width: 50%;
    background-image: url(https://i.imgur.com/LA17um6.png);
    width: 50%;
    background-position: right;
    background-size: 30%;
    background-repeat: no-repeat;
    background-position-x: 95%;
    color: white;
}

a.cy {
    background: #E1597F;
    padding: 50px;
    border-radius: 23px;
    background-image: url(https://i.imgur.com/LA17um6.png);
    width: 50%;
    background-position: right;
    background-size: 30%;
    background-repeat: no-repeat;
    background-position-x: 95%;
    color: white;
}

.flex.justify-center.items-center.lg\:w-1\/2 {
    flex-direction: column;
}

.flex.flex-col.gap-2.w-60.sm\:w-72.text-\[10px\].sm\:text-xs.z-50 {
    display: none;
}



@import url("https://fonts.googleapis.com/css2?family=Sora:wght@100;200;300;400;500;600;700&display=swap");
@import url('https://fonts.googleapis.com/css2?family=Yatra+One&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Comfortaa:wght@300..700&family=Noto+Color+Emoji&family=Red+Rose:wght@300..700&display=swap');

li {
    margin-top: 10px;
}

span.bg-red-400.mt-3.rounded-sm.px-5.py-1 {
    position: absolute;
    left: 25%;
    top: 10%;
    border-radius: 13px;
    background: hsla(39,100%,68%,1);
    z-index: 444;
    filter: drop-shadow(2px 4px 6px black);
}

.rounded-checkbox {
  width: 20px;
  height: 20px;
  background-color: #fff;
  border: 2px solid #ccc;
  border-radius: 50%; /* This will round the borders */
  display: inline-block;
  position: relative;
  cursor: pointer;
}

button.cursor-pointer.relative.p-3.border-2.border-white.overflow-hidden.bg-gradient-to-tr.from-yellow-100.to-yellow-200.group.duration-300.hover\:-rotate-45.hover\:opacity-75.hover\:scale-125.active\:scale-100.rounded-full.drop-shadow-xl {
    position: fixed;
    bottom: 4%;
    right: 6%;
}

@keyframes hue-rotate-animation {
  0% {
    filter: hue-rotate(0deg);
  }
  50% {
    filter: hue-rotate(353deg);
  }
  100% {
    filter: hue-rotate(0deg);
  }
}

.rounded-checkbox::after {
  content: "";
  position: absolute;
  top: 2px;
  left: 6px;
  width: 5px;
  height: 10px;
  border: solid #000;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
  opacity: 0;
}

input[type="checkbox"].hidden:checked + .rounded-checkbox::after {
  opacity: 1;
}
    

.cta {
border-radius: 13px;
    color: #fff;
    display: inline-block;
    font-family: "Sora";
    font-size: 1em;
    font-weight: 200;
    margin-bottom: 1em;
    padding: .3em 1em;
    position: absolute;
    right: 2%;
    TOP: 2%;
    z-index: 4;
    background-image: url(https://cdn3d.iconscout.com/3d/premium/thumb/solana-10229260-8263859.png?f=webp);
    background-size: 30%;
    height: 90px;
    background-repeat: no-repeat;
    width: 200px;
    background-position: 100%;
    -webkit-backdrop-filter: blur(4px);
    backdrop-filter: blur(4px);
    zoom: 60%;
}
.cta:hover {
  
}




.modaloverlay {
  background: rgba(0, 0, 0, 0.8);
  bottom: 0;
  left: 0;
  opacity: 0;
  pointer-events: none;
  position: fixed;
  right: 0;
  top: 0;
  -webkit-transition: opacity 400ms ease-in;
  -moz-transition: opacity 400ms ease-in;
  transition: opacity 400ms ease-in;
  z-index: -1;
  display: none;
}
.modaloverlay:target {
  display: block;
  opacity: 1;
  pointer-events: auto;
  z-index: 99999;
}
.modaloverlay .modal {
background-color: #121212;
    height: 100%;
    position: relative;
    margin: 0 auto;   
    background-size: 30%;
    padding: 3em;
    color:white;
    background-repeat: no-repeat;
    overflow:hidden;
    border-radius: 23px;
    border: 3px solid white;
    -webkit-backdrop-filter: blur(9px);
    backdrop-filter: blur(9px);
    background-position: 100% 100%;
}
@media (min-width: 60em) {
  .modaloverlay .modal {
    height: 75%;
    margin: 5% auto;
    max-height: 57em;
    max-width: 66em;
    width: 85%;
    margin-top:180px;
  }
}
.modaloverlay .modal > iframe, .modaloverlay .modal > div {
  border: none;
  width: 100%;
  
}
.modaloverlay .close {
background-color: #ff000000;
    color: #fff;
    font-size: 24px;
    padding: 8px 18px;
    position: absolute;
    right: 10px;
    text-align: center;
    text-decoration: none;
    top: 10px;
    z-index: 1;
    border-radius: 23px;
}







.modaloverlayy {
  background: rgba(0, 0, 0, 0.8);
  bottom: 0;
  left: 0;
  opacity: 0;
  pointer-events: none;
  position: fixed;
  right: 0;
  top: 0;
  -webkit-transition: opacity 400ms ease-in;
  -moz-transition: opacity 400ms ease-in;
  transition: opacity 400ms ease-in;
  z-index: -1;
  display: none;
}
.modaloverlayy:target {
  display: block;
  opacity: 1;
  pointer-events: auto;
  z-index: 99999;
}
.modaloverlayy .modal {

    height: 100%;
    position: relative;
    margin: 0 auto;   
    background-size: 30%;
    padding: 3em;
    color:white;
    background-repeat: no-repeat;
    overflow:hidden;
    border-radius: 23px;
    background-position: 100% 100%;
}
@media (min-width: 60em) {
  .modaloverlayy .modal {
    height: 75%;
    margin: 5% auto;
    max-height: 57em;
    max-width: 66em;
    width: 85%;
    margin-top:180px;
  }
}
.modaloverlayy .modal > iframe, .modaloverlayy .modal > div {
  border: none;
  width: 100%;
  
}
.modaloverlayy .close {
background-color: #ff000000;
    color: #fff;
    font-size: 24px;
    padding: 8px 18px;
    position: absolute;
    right: 10px;
    text-align: center;
    text-decoration: none;
    top: 10px;
    z-index: 1;
    border-radius: 23px;
}







html {
    display: block;
    backdrop-filter: brightness(0.7);
}

p.call {
    font-size: 3em;
    margin-top: 22px;
}

.bdr-ripple-ani-btn {
    display: block;
    background: #5B9BFF;
    width: 68px;
    height: 68px;
    line-height: 48px;
    text-align: center;
    border-radius: 100%;
    box-sizing: border-box;
    color: #666;
    animation: at-ripple 0.6s linear infinite;
    overflow: hidden;
    border: 2px SOLID #5B9BFF;
}
.bdr-ripple-ani-btn.pink {
  background: #ff4081;
  color:white;
  animation: at-ripple-pink 0.6s linear infinite;

}
.bdr-ripple-ani-btn.two {
  right: 300px;
  z-index: 2;
  position: fixed;
  bottom: 50px;
}
.bdr-ripple-ani-btn i {
  transform: rotate(0deg);
  transition: 0.5s ease;
}
.bdr-ripple-ani-btn:hover i {
  transform: rotate(180deg);
}
@-webkit-keyframes at-ripple {
  0% {
    box-shadow: 0 4px 10px rgba(102, 102, 102, 0.1), 0 0 0 0 rgba(102, 102, 102, 0.1), 0 0 0 5px rgba(102, 102, 102, 0.1), 0 0 0 10px rgba(102, 102, 102, 0.1);
  }
  100% {
    box-shadow: 0 4px 10px rgba(102, 102, 102, 0.1), 0 0 0 5px rgba(102, 102, 102, 0.1), 0 0 0 10px rgba(102, 102, 102, 0.1), 0 0 0 20px rgba(102, 102, 102, 0);
  }
}
@keyframes at-ripple {
  0% {
    box-shadow: 0 4px 10px rgba(102, 102, 102, 0.1), 0 0 0 0 rgba(102, 102, 102, 0.1), 0 0 0 5px rgba(102, 102, 102, 0.1), 0 0 0 10px rgba(102, 102, 102, 0.1);
  }
  100% {
    box-shadow: 0 4px 10px rgba(102, 102, 102, 0.1), 0 0 0 5px rgba(102, 102, 102, 0.1), 0 0 0 10px rgba(102, 102, 102, 0.1), 0 0 0 20px rgba(102, 102, 102, 0);
  }
}
/* Pink Animate */
@-webkit-keyframes at-ripple-pink {
  0% {
    box-shadow: 0 4px 10px rgba(255, 65, 130, 0.1), 0 0 0 0 rgba(255, 65, 130, 0.1), 0 0 0 5px rgba(255, 65, 130, 0.1), 0 0 0 10px rgba(255, 65, 130, 0.1);
  }
  100% {
    box-shadow: 0 4px 10px rgba(255, 65, 130, 0.1), 0 0 0 5px rgba(255, 65, 130, 0.1), 0 0 0 10px rgba(255, 65, 130, 0.1), 0 0 0 20px rgba(255, 65, 130, 0);
  }
}
@keyframes at-ripple-pink {
  0% {
    box-shadow: 0 4px 10px rgba(255, 65, 130, 0.1), 0 0 0 0 rgba(255, 65, 130, 0.1), 0 0 0 5px rgba(255, 65, 130, 0.1), 0 0 0 10px rgba(255, 65, 130, 0.1);
  }
  100% {
    box-shadow: 0 4px 10px rgba(255, 65, 130, 0.1), 0 0 0 5px rgba(255, 65, 130, 0.1), 0 0 0 10px rgba(255, 65, 130, 0.1), 0 0 0 20px rgba(255, 65, 130, 0);
  }
}



.glow-shadow {
    background:#fff;
    width:100px;
    height:100px;
    left:50px;
    margin-left:50px;
    margin-top:15%;
    border-radius:50%;
    -webkit-animation: throb 1.5s infinite ease-in-out;
    animation: glow 1.5s infinite ease-in-out;
}
@-webkit-keyframes glow {
    0% {
        -webkit-box-shadow: 0 0 50px 50px rgba(50, 160, 50, 0.9);
    }
    50% {
        -webkit-box-shadow: 0 0 50px 0px rgba(50, 160, 50, .2);
    }
    100% {
        -webkit-box-shadow: 0 0 50px 50px rgba(50, 160, 50, 0.9);
    }
}
@keyframes glow {
    0% {
        box-shadow: 0 0 50px rgba(50, 160, 50, 0.9);
    }
    50% {
        box-shadow: 0 0 50px rgba(50, 160, 50, .2);
    }
    100% {
        box-shadow: 0 0 50px rgba(50, 160, 50, 0.9);
    }
}

@-webkit-keyframes float {
  0% {
    transform: translatey(0px);
    transform: translatex(0px);
  }
  50% {
    transform: translatey(-30px);
    transform: translatex(20px);
  }
  100% {
    transform: translatey(0px);
    transform: translatex(0px);
  }
}
@-moz-keyframes float {
  0% {
    transform: translatey(0px);
    transform: translatex(0px);
  }
  50% {
    transform: translatey(-30px);
    transform: translatex(20px);
  }
  100% {
    transform: translatey(0px);
    transform: translatex(0px);
  }
}
@-o-keyframes float {
  0% {
    transform: translatey(0px);
    transform: translatex(0px);
  }
  50% {
    transform: translatey(-30px);
    transform: translatex(20px);
  }
  100% {
    transform: translatey(0px);
    transform: translatex(0px);
  }
}
@keyframes float {
  0% {
    transform: translatey(0px);
    transform: translatex(0px);
  }
  50% {
    transform: translatey(-30px);
    transform: translatex(20px);
  }
  100% {
    transform: translatey(0px);
    transform: translatex(0px);
  }
}
*, *:before, *:after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.button {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 2;
}
.button button {
  position: absolute;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  -moz-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  -o-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  font-family: inherit;
  border-radius: 23pc;
  background-color: #ffffff;
  border: 0;
  padding: 15px 25px;
  color: #000000;
  text-transform: uppercase;
  font-size: 21px;
  letter-spacing: 1px;
  width: 200px;
  overflow: hidden;
  outline: 0;
  -webkit-transition: all 0.4s;
  -moz-transition: all 0.4s;
  -o-transition: all 0.4s;
  transition: all 0.4s;
  visibility: visible;
  opacity: 1;
  font-weight: bold;
  box-shadow: 0px 6px 30px rgba(0, 0, 0, 0.6);
}
.button button:hover {
  cursor: pointer;
  background-color: #222;
  color: #ffffff;
}
.button button span {
  opacity: 1;
  font-family: Comfortaa;
}
.button.clicked button {
  visibility: hidden;
  oacity: 0;
}

.pop-up {
  position: absolute;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%) scale(0.9);
  -moz-transform: translate(-50%, -50%) scale(0.9);
  -ms-transform: translate(-50%, -50%) scale(0.9);
  -o-transform: translate(-50%, -50%) scale(0.9);
  transform: translate(-50%, -50%) scale(0.9);
  overflow-y: auto;
  box-shadow: 0px 6px 30px rgba(0, 0, 0, 0.4);
  visibility: hidden;
  opacity: 0;
  -webkit-transition: all 0.3s;
  -moz-transition: all 0.3s;
  -o-transition: all 0.3s;
  transition: all 0.3s;
  z-index: 10;
  background-color: #ffffff;
  width: 100%;
  height: 100%;
}
@media (min-width: 768px) {
  .pop-up {
    width: calc(100% - 40px);
    height: auto;
    max-width: 900px;
  }
}
.pop-up .content {
  width: 100%;
  max-width: 900px;
  overflow: hidden;
  text-align: center;
  position: relative;
  min-height: 100vh;
}
@media (min-width: 768px) {
  .pop-up .content {
    min-height: inherit;
  }
}
.pop-up .content .container {
  padding: 100px 20px 140px;
}
@media (min-width: 568px) {
  .pop-up .content .container {
    padding: 50px 20px 80px;
  }
}
@media (min-width: 768px) {
  .pop-up .content .container {
    padding: 70px 0px 90px;
    max-width: 520px;
    margin: 0 auto;
  }
}
.pop-up .content .close {
  position: absolute;
    top: 20px;
    left: 20px;
    font-size: 1.1rem;
    letter-spacing: 0.05rem;
    color: #222;
    -webkit-transition: all 0.4s;
    -moz-transition: all 0.4s;
    -o-transition: all 0.4s;
    transition: all 0.4s;
    font-weight: 400;
}
.pop-up .content .close:hover {
  cursor: pointer;
  color: #bcbcbc;
}
.pop-up .content .dots .dot {
  position: absolute;
  border-radius: 100%;
  z-index: 11;
}
.pop-up .content .dots .dot:nth-of-type(1) {
  top: -80px;
  right: -80px;
  width: 160px;
  height: 160px;
  background-color: #ffb4ce;
  -webkit-animation: float 6s ease-in-out infinite;
  -moz-animation: float 6s ease-in-out infinite;
  -o-animation: float 6s ease-in-out infinite;
  animation: float 6s ease-in-out infinite;
}
@media (min-width: 768px) {
  .pop-up .content .dots .dot:nth-of-type(1) {
    top: -190px;
    right: -190px;
    width: 380px;
    height: 380px;
  }
}
.pop-up .content .dots .dot:nth-of-type(2) {
  bottom: -120px;
  left: -120px;
  width: 240px;
  height: 240px;
  background-color: #fff38e;
  -webkit-animation: float 8s ease-in-out infinite;
  -moz-animation: float 8s ease-in-out infinite;
  -o-animation: float 8s ease-in-out infinite;
  animation: float 8s ease-in-out infinite;
}
.pop-up .content .dots .dot:nth-of-type(3) {
  bottom: -50px;
  right: -50px;
  width: 100px;
  height: 100px;
  background-color: #82d8ff;
  -webkit-animation: float 4s ease-in-out infinite;
  -moz-animation: float 4s ease-in-out infinite;
  -o-animation: float 4s ease-in-out infinite;
  animation: float 4s ease-in-out infinite;
}
.pop-up .content .title h1 {
  text-align: center;
  color: #bcbcbc;
  text-transform: uppercase;
  font-weight: 900;
  font-size: 2.8rem;
  letter-spacing: 0.05rem;
}
.pop-up .content img {
  width: 100%;
  max-width: 220px;
  display: inline-block;
  margin: 30px 0 40px 0;
  opacity: 0;
  -webkit-transform: translateX(60px);
  -moz-transform: translateX(60px);
  -ms-transform: translateX(60px);
  -o-transform: translateX(60px);
  transform: translateX(60px);
  -webkit-transition: 0.2s;
  -moz-transition: 0.2s;
  -o-transition: 0.2s;
  transition: 0.2s;
  -webkit-backface-visibility: hidden;
}
@media (min-width: 768px) {
  .pop-up .content img {
    max-width: 300px;
  }
}
.pop-up .content .subscribe h1 {
  font-size: 1.5rem;
  color: #222;
  line-height: 130%;
  letter-spacing: 0.07rem;
  margin-bottom: 30px;
}
.pop-up .content .subscribe h1 span {
  color: #bcbcbc;
}
.pop-up .content .subscribe form {
  overflow: hidden;
}
.pop-up .content .subscribe form input {
  width: 100%;
  float: left;
  padding: 15px 20px;
  text-align: center;
  font-family: inherit;
  font-size: 1.1rem;
  letter-spacing: 0.05rem;
  outline: 0;
}
.pop-up .content .subscribe form input[type=email] {
  margin-bottom: 15px;
  border-radius: 23PC 0PC 0PC 23PC;
  border: 1px solid #a2a2a2;
  -webkit-transition: all 0.4s;
  -moz-transition: all 0.4s;
  -o-transition: all 0.4s;
  transition: all 0.4s;
}
@media (min-width: 768px) {
  .pop-up .content .subscribe form input[type=email] {
    margin-bottom: 0px;
    width: 75%;
    border-right-width: 0px;
  }
}
.pop-up .content .subscribe form input[type=email]:focus {
  border-color: #222;
}
.pop-up .content .subscribe form input[type=submit] {
    background-color: #1f1f1f8c;
    color: #ffffff;
    border-radius: 0PC 23PC 23PC 0PC;
    /* border: 1px solid #222; */
    -webkit-transition: all 0.4s;
    -moz-transition: all 0.4s;
    -o-transition: all 0.4s;
    transition: all 0.4s;
}
@media (min-width: 768px) {
  .pop-up .content .subscribe form input[type=submit] {
    width: 25%;
  }
}
.pop-up .content .subscribe form input[type=submit]:hover {
  cursor: pointer;
  background-color: #090909;
  border-color: #090909;
}
.pop-up.open {
  visibility: visible;
  border-radius:23px;
  opacity: 1;
  position: fixed;
  -webkit-transform: translate(-50%, -50%) scale(1);
  -moz-transform: translate(-50%, -50%) scale(1);
  -ms-transform: translate(-50%, -50%) scale(1);
  -o-transform: translate(-50%, -50%) scale(1);
  transform: translate(-50%, -50%) scale(1);
  cursor: url(https://i.imgur.com/IyBiS1B.png) 25 15, auto;
}
.pop-up.open img {
  margin-bottom: 0;
  opacity: 1;
  -webkit-transition: 1s;
  -moz-transition: 1s;
  -o-transition: 1s;
  transition: 1s;
  -webkit-transition-delay: 0.3s;
  -moz-transition-delay: 0.3s;
  -o-transition-delay: 0.3s;
  transition-delay: 0.3s;
  -webkit-transform: translateX(0px);
  -moz-transform: translateX(0px);
  -ms-transform: translateX(0px);
  -o-transform: translateX(0px);
  transform: translateX(0px);
}

p.back {
      font-size: 8EM;
    position: fixed;
    opacity: 0.8;
    COLOR: #1f1f1f;
    font-weight: 600;
    font-family: 'Russo One', sans-serif;
}


.red-rose-<uniquifier> {
  font-family: "Red Rose", serif;
  font-optical-sizing: auto;
  font-weight: <weight>;
  font-style: normal;
}

[data-tooltip]:after {
    content: attr(data-tooltip);
    text-align: center;
    min-width: 3em;
    max-width: 21em;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    padding: 6px 8px;
    border-radius: 3px;
    background: #222;
    color: #000;
    z-index: 100;
    margin-left: 10px;
}


div#google1:hover {
    background: rgb(0 0 0 / 95%);
    transform: scale(1.2);
    transition: 2s;
}

.box {
  width: 200px; height: 300px;
  position: relative;
  border: 1px solid #BBB;
  background: #EEE;
}
.ribbon {
  position: absolute;
  right: -5px; top: -5px;
  z-index: 1;
  overflow: hidden;
  width: 75px; height: 75px;
  text-align: right;
}
.ribbon span {
  font-size: 10px;
    font-weight: 700;
    color: #000;
    text-transform: none;
    text-align: center;
    line-height: 20px;
    transform: rotate(45deg);
    -webkit-transform: rotate(45deg);
    width: 100px;
    display: block;
    background: #fff;
    box-shadow: 0 3px 10px -5px #000;
    position: absolute;
    top: 19px;
    right: -21px;
    font-family: "Sora";
    text-transform: uppercase;
}

.ribbon span::before {
  content: "";
  position: absolute; left: 0px; top: 100%;
  z-index: -1;
  border-left: 3px solid #000;
  border-right: 3px solid transparent;
  border-bottom: 3px solid transparent;
  border-top: 3px solid #000;
}
.ribbon span::after {
  content: "";
  position: absolute; right: 0px; top: 100%;
  z-index: -1;
  border-left: 3px solid transparent;
  border-right: 3px solid #000;
  border-bottom: 3px solid transparent;
  border-top: 3px solid #000;
}

.glitch-wrapper {
   width: 100%;
   height: 100%;
   display: flex;
   align-items: center;
   justify-content: center;
   text-align: center;
   
}

.circle {
  --circle-size: 40px;
  position: fixed;
  height: var(--circle-size);
  width: var(--circle-size);
  border: 1px solid white;
  border-radius: 100%;
  top: calc(var(--circle-size) / 2 * -1);
  left: calc(var(--circle-size) / 2 * -1);
  pointer-events: none;
}

[data-tooltip] {
  position: relative;
  pointer: cursor;
  color:white;
  z-index:222;
}
[data-tooltip]::before,
[data-tooltip]::after {
  text-transform: none;
  font-size: .9em;
  line-height: 1;
  position: absolute;
  display: none;
  opacity: 0;
}
[data-tooltip]::before {
  content: '';
  border: 6px solid transparent;
  z-index: 101;
}
[data-tooltip]::after {
  content: attr(data-tooltip);
  text-align: center;
  min-width: 3em;
  max-width: 21em;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  padding: 6px 8px;
  border-radius: 3px;
  background: #FFFFFF;
  color: #FFFFFF;
  z-index: 100;
}
[data-tooltip]:hover::before,
[data-tooltip]:hover::after {
  display: block;
}
[data-tooltip='']::before,
[data-tooltip='']::after {
  display: none !important;
}
[data-tooltip]:not([data-flow])::before,
[data-tooltip][data-flow^="top"]::before {
  bottom: 100%;
  border-bottom-width: 0;
  border-top-color: #333333;
}
[data-tooltip]:not([data-flow])::after,
[data-tooltip][data-flow^="top"]::after {
  bottom: calc(100% + 5px);
}
[data-tooltip]:not([data-flow])::before,
[data-tooltip]:not([data-flow])::after,
[data-tooltip][data-flow^="top"]::before,
[data-tooltip][data-flow^="top"]::after {
  
  transform: translate(-50%, -.4em);
  left: 20%;
    top: 130%;
    transform: translate(-50%, 0.4em);
    background: #333333;
    filter: drop-shadow(2px 4px 6px black);
}
[data-tooltip][data-flow^="bottom"]::before {
  top: 100%;
  border-top-width: 0;
  border-bottom-color: #333333;
}
[data-tooltip][data-flow^="bottom"]::after {
  top: calc(100% + 5px);
}
[data-tooltip][data-flow^="bottom"]::before,
[data-tooltip][data-flow^="bottom"]::after {
  left: 50%;
  transform: translate(-50%, .4em);
}
[data-tooltip][data-flow^="left"]::before {
  top: 50%;
  border-right-width: 0;
  border-left-color: #333333;
  left: calc(0em - 5px);
  transform: translate(-.5em, -50%);
}
[data-tooltip][data-flow^="left"]::after {
  top: 50%;
  right: calc(100% + 5px);
  transform: translate(-.4em, -50%);
}
[data-tooltip][data-flow^="right"]::before {
  top: 50%;
  border-left-width: 0;
  border-right-color: #333333;
  right: calc(0em - 7px);
  transform: translate(.4em, -50%);
}
[data-tooltip][data-flow^="right"]::after {
  top: 50%;
  left: calc(100% + 5px);
  transform: translate(.5em, -50%);
}
@keyframes tooltip-vert {
  to {
    opacity: 1;
    transform: translate(-50%, 0);
  }
}
@keyframes tooltip-horz {
  to {
    opacity: 1;
    transform: translate(0, -50%);
  }
}
[data-tooltip]:not([data-flow]):hover::before,
[data-tooltip]:not([data-flow]):hover::after,
[data-tooltip][data-flow^="top"]:hover::before,
[data-tooltip][data-flow^="top"]:hover::after,
[data-tooltip][data-flow^="bottom"]:hover::before,
[data-tooltip][data-flow^="bottom"]:hover::after {
  animation: tooltip-vert .5s ease-out forwards;
    left: 20%;
    top: 130%;
    transform: translate(-50%, 0.4em);
    background: #333333;
    filter: drop-shadow(2px 4px 6px black);
}
[data-tooltip][data-flow^="left"]:hover::before,
[data-tooltip][data-flow^="left"]:hover::after,
[data-tooltip][data-flow^="right"]:hover::before,
[data-tooltip][data-flow^="right"]:hover::after {
  animation: tooltip-horz .5s ease-out forwards;
}

div#app:hover {
    
}

.glitch {
   position: relative;
   font-size: 40px;
   font-weight: bold;
   color: #FFFFFF;
   letter-spacing: 3px;
   z-index: 0;
   filter: drop-shadow(-9px -10px 4px black);
}

.glitch:before,
.glitch:after {
   display: block;
   content: attr(data-text);
   position: absolute;
   top: 0;
   left: 0;
   opacity: 0.8;
   font-family: ui-sans-serif, system-ui, sans-serif, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;
}

.glitch:before {
   animation: glitch-it 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94) both infinite;
   color: #00FFFF;
   z-index: -1;
   font-family: ui-sans-serif, system-ui, sans-serif, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;
}

.glitch:after {
   animation: glitch-it 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94) reverse both infinite;
   color: #FF00FF;
   z-index: -2;
}

@keyframes glitch-it {
   0% {
      transform: translate(0);
   }
   20% {
      transform: translate(-2px, 2px);
   }
   40% {
      transform: translate(-2px, -2px);
   }
   60% {
      transform: translate(2px, 2px);
   }
   80% {
      transform: translate(2px, -2px);
   }
   to {
      transform: translate(0);
   }
}

.closeflag {
  display: none;
}

.closebutton {
  float: right;
  cursor: pointer;
  font-size: 1.5em;
    margin-left: 20px;
}

.closeflag:checked+.msgbox {
  display: none;
}

/* For demonstration purposes: */
.msgbox {
    border: 2px solid black;
    border-radius: 4px;
    padding: 19px;
    background-image: url(https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExcGlxNm1md2diMnkxMXdwazR3cHh5MXA4Y21ncGlwMG9rcjhndzhwbSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xTiTniuHdUjpOlNo1q/giphy.gif);
    background-size: 100%;
    background-color: #00000078;
    color: white;
    background-position: bottom !important;
    filter: drop-shadow(2px 4px 6px black);
}

.accordion {
    display: flex;
    flex-direction: column;
    
    max-width: 991px;
    min-width: 320px;
    margin: 50px auto;
    padding: 0 50px;
}
.accordion h1 {
    font-size: 32px;
    text-align: center;
}

use.text {
    stroke-width: 2px;
}

.button-85 {
  padding: 0.6em 2em;
  border: none;
  outline: none;
  color: rgb(255, 255, 255);
  background: #111;
  cursor: pointer;
  position: relative;
  z-index: 0;
  border-radius: 10px;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.button-85:before {
  content: "";
    
    position: absolute;
    top: -2px;
    left: -2px;
    background-size: 400%;
    z-index: -1;
    filter: blur(5px);
    -webkit-filter: blur(5px);
    width: calc(100% + 4px);
    height: calc(100% + 4px);
    animation: glowing-button-85 20s linear infinite;
    transition: opacity .3s ease-in-out;
    border-radius: 10px;
}

@keyframes glowing-button-85 {
  0% {
    background-position: 0 0;
  }
  50% {
    background-position: 400% 0;
  }
  100% {
    background-position: 0 0;
  }
}

.button-85:after {
 z-index: -1;
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    
    left: 0;
    top: 0;
    border-radius: 10px;
}

button.button-85.bg-blue-500.hover\:bg-blue-700.text-white.font-bold.py-3.px-4.rounded.w-full.mt-3.mb-4.bg-gradient-to-r.from-\[\#2152ff\].to-\[\#21d4fd\].uppercase.hover\:scale-\[1\.01\].duration-100:hover {
    transform: scale(0.9);
}

button.bg-blue-500.hover\:bg-blue-700.text-white.font-bold.py-3.px-4.rounded.w-full.mt-3.mb-4.bg-gradient-to-r.from-\[\#2152ff\].to-\[\#21d4fd\].uppercase.hover\:scale-\[1\.01\].duration-100 {
 text-transform: inherit;
    background-image: linear-gradient(348deg, #18ffa5 30%, #830cff);
    color: #fff;
    margin-top: 40px;
    font-weight: 300;
    top: -70px;
    width: 75%;
    z-index: 444;
    margin-left: auto;
    box-shadow: 8px 8px hsla(39, 100%, 68%, 1);
    margin-right: auto;
    background: #373736;
    font-family: "Sora"!important;
}



.flex.flex-col.mt-5.border.border-gray-300.p-10.rounded-lg.shadow-lg.shadow-gray-500.w-\[550px\] 

{
    transition: 2s;
    margin-right: 20%;
    width: 80%;
    margin-left: auto;
    margin-right: auto;
    height:400px;
    max-height: 600px;
    padding-top: 20px;
    filter: drop-shadow(2px 4px 6px black);
    border: none;
    background-position: bottom;
    background: url(https://media-private.canva.com/3oeDY/MAFBem3oeDY/1/s2.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAJWF6QO3UH4PAAJ6Q%2F20240615%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240615T144530Z&X-Amz-Expires=30565&X-Amz-Signature=0e0f782%E2%80%A6&X-Amz-SignedHeaders=host%3Bx-amz-expected-bucket-owner&response-expires=Sat%2C%2015%20Jun%202024%2023%3A14%3A55%20GMT);
    background-size: 0;
    background-color: #fff;
    color: #000;
    background-repeat: no-repeat;
    background-position-x: right;
    background-position-y: bottom;
    -webkit-backdrop-filter: blur(4px);
    box-shadow: 8px 8px #fff;
    border: 1px solid #000;
    backdrop-filter: blur(4px);
}

.flex.flex-col.mt-5.border.border-gray-300.p-10.rounded-lg.shadow-lg.shadow-gray-500.w-\[550px\]:hover {
    

    
}

div#app {
    dispay:flex;
    background-image: url(https://i.imgur.com/WrJcCVq.png);
    background-position:bottom left;
    background-size: 35%;
    background-color: #ffffff00;
    background-repeat: no-repeat;
}

.over {
    display:none;
  }






























p.nop {
    
    margin-top: 290px;
    position: absolute;
    text-align: center;
    margin-left: 60px;

}


col.mt-5.border.border-gray-300.p-10.rounded-lg.shadow-lg.shadow-gray-500.w-\[550px\] {
    transform: scale(2) translateX(-150px);
    transition: 2s;
    width:100%;
}


.bk {
width: 100%;
    height: 100%;
    
}

.accordion-item {
    margin-top: 16px;
    border: 1px solid #fcfcfc;
    border-radius: 6px;
    background: #ffffff;
    box-shadow: rgba(0, 0, 0, 0.05) 0px 1px 2px 0px;
}
.accordion-item .accordion-item-title {
    position: relative;
    margin: 0;
    display: flex;
    width: 100%;
    font-size: 15px;
    cursor: pointer;
    justify-content: space-between;
    flex-direction: row-reverse;
    padding: 14px 20px;
    box-sizing: border-box;
    align-items: center;
}
.accordion-item .accordion-item-desc {
    display: none;
    font-size: 14px;
    line-height: 22px;
    font-weight: 300;
    color: #444;
    border-top: 1px dashed #ddd;
    padding: 10px 20px 20px;
    box-sizing: border-box;
}
.accordion-item input[type="checkbox"] {
    position: absolute;
    height: 0;
    width: 0;
    opacity: 0;
}
.accordion-item input[type="checkbox"]:checked ~ .accordion-item-desc {
    display: block;
}
.accordion-item
    input[type="checkbox"]:checked
    ~ .accordion-item-title
    .icon:after {
    content: "-";
    font-size: 20px;
}
.accordion-item input[type="checkbox"] ~ .accordion-item-title .icon:after {
    content: "+";
    font-size: 20px;
}
.accordion-item:first-child {
    margin-top: 0;
}
.accordion-item .icon {
    margin-left: 14px;
}


</style>

<style>
.ring {
  position: relative;
  width: 400px;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.ring i {
    position: absolute;
    inset: 0;
    transition: 0.5s;
    border: 6px solid white;
    filter: drop-shadow(0 0 20px #ffc65c);
}
.ring i:nth-child(1) {
  border-radius: 38% 62% 63% 37% / 41% 44% 56% 59%;
  animation: animate 6s linear infinite;
}
.ring i:nth-child(2) {
  border-radius: 41% 44% 56% 59%/38% 62% 63% 37%;
  animation: animate 4s linear infinite;
}
.ring i:nth-child(3) {
  border-radius: 41% 44% 56% 59%/38% 62% 63% 37%;
  animation: animate2 10s linear infinite;
}
.ring:hover i {
  border: 6px solid var(--clr);
  filter: drop-shadow(0 0 20px var(--clr));
}
@keyframes animate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
@keyframes animate2 {
  0% {
    transform: rotate(360deg);
  }
  100% {
    transform: rotate(0deg);
  }
}
</style>








<style type="text/css">/*
! tailwindcss v3.4.3 | MIT License | https://tailwindcss.com
*//*
1. Prevent padding and border from affecting element width. (https://github.com/mozdevs/cssremedy/issues/4)
2. Allow adding a border to an element by just adding a border-width. (https://github.com/tailwindcss/tailwindcss/pull/116)
*/

@import url('https://fonts.googleapis.com/css2?family=Comfortaa:wght@300..700&display=swap');

@import url('https://fonts.googleapis.com/css2?family=Overlock+SC&display=swap');

.flex.flex-col.lg\:w-1\/2.justify-center.items-center.w-full {
    margin-top: -350px;
}

*,
::before,
::after {
  box-sizing: border-box; /* 1 */
  border-width: 0; /* 2 */
  border-style: solid; /* 2 */
  border-color: #e5e7eb; /* 2 */
}

::before,
::after {
  --tw-content: '';
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

h1.tt.text-5xl.font-sans.text-slate-800.font-bold.text-center.text-transparent.bg-clip-text.bg-gradient-to-l.from-\[\#7928ca\].to-\[\#ff0080\] {
    font-weight: 900;

}

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
  background-image: url(https://i.imgur.com/Au3ROiu.jpeg);
    background-size: 170%;
    background-position: left;
    backdrop-filter: blur(11px);
   
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

.swv-button[disabled] {
    background: white!important;
    color: black!important;
    cursor: not-allowed;
}
.swv-modal-overlay {
    background: #0000007a;
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    margin-top: -100px;
    right: 0;
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
  --tw-ring-color: #451f1f00!important;
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
.visible {
  visibility: visible;
}
.collapse {
  visibility: collapse;
}
.relative {
  position: relative;
}
.mb-4 {
  margin-bottom: 1rem;
}
.mt-10 {
    margin-bottom: 50px;
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
.table {
  display: table;
}
.contents {
  display: contents;
}
.hidden {
  display: none;
}
.h-5 {
  height: 1.25rem;
}
.h-screen {
  height: 100vh;
}
.w-1\/3 {
  width: 33.333333%;
  
}
.w-1\/4 {
  width: 25%;
}
.w-3\/4 {
  width: 65%;
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
.w-1 {
  width: 0.25rem;
}
.w-3 {
  width: 0.75rem;
}
.border-collapse {
  border-collapse: collapse;
}
.transform {
  transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
}
.resize {
  resize: both;
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
.border-gray-600 {
  --tw-border-opacity: 1;
  border-color: rgb(75 85 99 / var(--tw-border-opacity));
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
.bg-gray-700 {
  --tw-bg-opacity: 1;
  background-color: rgb(55 65 81 / var(--tw-bg-opacity));
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
  
}
.to-\[\#21d4fd\] {
  --tw-gradient-to: #21d4fd var(--tw-gradient-to-position);
}
.to-\[\#ff0080\] {
          --tw-gradient-to: #ffffff00!important;
    --tw-gradient-from: #27ff8b00!important;
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
.px-36 {
  padding-left: 9rem;
  padding-right: 9rem;
}
.pl-4 {
  padding-left: 1rem;
}
.pr-4 {
  padding-right: 1rem;
}
.text-center {
  text-align: center;
  color:white;
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
.leading-6 {
  line-height: 1.5rem;
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
  color: white !important;
}
.text-white {
  --tw-text-opacity: 1;
  color: rgb(255 255 255 / var(--tw-text-opacity));
}
.underline {
  text-decoration-line: underline;
}
.shadow-lg {
  --tw-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --tw-shadow-colored: 0 10px 15px -3px var(--tw-shadow-color), 0 4px 6px -4px var(--tw-shadow-color);
  box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow);
}
.shadow-gray-500 {
  --tw-shadow-color: #black!important;
  --tw-shadow: var(--tw-shadow-colored);
}
.outline {
  outline-style: solid;
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

  color:white!important;
  width:100%!important;
  box-shadow: 4px 4px black;
    border: 1px solid white;
    background: radial-gradient(#636363, black);
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

<style type="text/css">:root {
    /* Buttons. */
    --swv-button-background-color: #4f46e5;
    --swv-button-text-color: white;
    --swv-button-outline-color: #3730a3;
    --swv-button-hover-background-color: #4338ca;
    --swv-button-disabled-background-color: #475569;
    --swv-button-disabled-text-color: #94a3b8;

    /* Modal. */
    --swv-overlay-background-color: rgba(200, 200, 200, 0.8);
    --swv-modal-background-color: white;
    --swv-modal-text-color: #1f2937;
    --swv-modal-close-button-background-color: #f3f4f6;
    --swv-modal-close-button-text-color: #9ca3af;
    --swv-modal-close-button-hover-text-color: #374151;
    --swv-modal-button-text-color: #1f2937;
    --swv-modal-wallet-status-text-color: #64748b;
    --swv-modal-button-hover-background-color: #f3f4f6;
    --swv-modal-button-outline-color: var(--swv-button-outline-color);

    /* Dropdown. */
    --swv-dropdown-background-color: white;
    --swv-dropdown-item-hover-background-color: #f3f4f6;
    --swv-dropdown-text-color: #1f2937;

    /* Shadows. */
    --swm-modal-shadow: 0 25px 25px rgb(0 0 0 / 0.15);
    --swm-dropdown-shadow: 0px 10px 20px rgba(0, 0, 0, 0.3);

    /* Radius. */
    --swv-button-radius: 6px;
    --swv-modal-radius: 10px;
    --swv-dropdown-radius: 10px;
    --swv-dropdown-item-radius: 6px;
}

.swv-dark {
    /* Modal. */
    --swv-overlay-background-color: rgba(0, 0, 0, 0.7);
    --swv-modal-background-color: #1e293b;
    --swv-modal-text-color: white;
    --swv-modal-close-button-background-color: #0f172a;
    --swv-modal-close-button-text-color: #64748b;
    --swv-modal-close-button-hover-text-color: white;
    --swv-modal-button-text-color: white;
    --swv-modal-wallet-status-text-color: #64748b;
    --swv-modal-button-hover-background-color: #0f172a;
    --swv-modal-button-outline-color: white;

    /* Dropdown. */
    --swv-dropdown-background-color: #1e293b;
    --swv-dropdown-item-hover-background-color: #334155;
    --swv-dropdown-text-color: white;

    /* Shadows. */
    --swm-modal-shadow: 0px 8px 20px rgba(0, 0, 0, 0.6);
}

.swv-button {
    background-color: transparent;
    border: none;
    color: var(--swv-button-text-color);
    cursor: pointer;
    display: flex;
    align-items: center;
    font-family: 'DM Sans', 'Roboto', 'Helvetica Neue', Helvetica, Arial, sans-serif;
    font-size: 16px;
    font-weight: 600;
    height: 48px;
    line-height: 48px;
    padding: 0 24px;
    border-radius: var(--swv-button-radius);
}

.swv-button > * + * {
    margin-left: 12px;
}

.swv-button-trigger {
    background: white;
    color: black;
    font-family: monospace;
    
    font-weight: 100;
    transition:0.5s;
}

.swv-button:not([disabled]):hover {
    background-color: #ffffffdb !important;
    transition: 0.5s;
    transform: scale(1.2);
    border-radius: 13px;
}

.swv-button:not([disabled]):focus-visible {
    outline-color: var(--swv-button-outline-color);
}

.swv-button:not([disabled]):hover {
    background-color: var(--swv-button-hover-background-color);
}

.swv-button[disabled] {
    background: var(--swv-button-disabled-background-color);
    color: var(--swv-button-disabled-text-color);
    cursor: not-allowed;
}

.swv-button-icon,
.swv-button-icon img {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 24px;
    height: 24px;
}

.swv-dropdown {
    margin-left: auto;
    margin-right: auto;
    
}

.swv-dropdown-list {
    position: absolute;
    z-index: 99;
    display: grid;
    grid-template-rows: 1fr;
    grid-row-gap: 10px;
    padding: 10px;
    top: 100%;
    right: 0;
    margin: 0;
    list-style: none;
    background: var(--swv-dropdown-background-color);
    color: var(--swv-dropdown-text-color);
    border-radius: var(--swv-dropdown-radius);
    box-shadow: var(--swm-dropdown-shadow);
    opacity: 0;
    visibility: hidden;
    transition: opacity 200ms ease, transform 200ms ease, visibility 200ms;
    font-family: 'DM Sans', 'Roboto', 'Helvetica Neue', Helvetica, Arial, sans-serif;
}

.swv-dropdown-list-active {
    opacity: 1;
    visibility: visible;
    transform: translateY(10px);
}

.swv-dropdown-list-item {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    border: none;
    outline: none;
    cursor: pointer;
    white-space: nowrap;
    box-sizing: border-box;
    padding: 0 20px;
    width: 100%;
    border-radius: var(--swv-dropdown-item-radius);
    font-size: 14px;
    font-weight: 500;
    height: 37px;
}

.swv-dropdown-list-item:not([disabled]):hover {
    background-color: var(--swv-dropdown-item-hover-background-color);
}

.swv-modal-collapse-button {
    justify-content: space-between;
    border-radius: 0px 0px var(--swv-modal-radius) var(--swv-modal-radius);
}

.swv-modal-collapse-button svg {
    transition: transform ease-in 150ms;
    align-self: center;
    fill: #999;
}

.swv-modal-collapse-button.swv-modal-collapse-button-active svg {
    transform: rotate(180deg);
}

.swv-modal {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    opacity: 1;
    transition: opacity linear 150ms;
    z-index: 99999;
    overflow-y: auto;
}

.swv-modal-logo-wrapper {
    padding: 60px;
    padding-bottom: 0px;
}

.swv-modal-logo {
    max-width: 100%;
    max-height: 100px;
}

.swv-modal-button-close {
    display: flex;
    align-items: center;
    justify-content: center;
    position: absolute;
    top: 18px;
    right: 18px;
    padding: 12px;
    cursor: pointer;
    background: var(--swv-modal-close-button-background-color);
    color: var(--swv-modal-close-button-text-color);
    border: none;
    border-radius: 50%;
}

.swv-modal-button-close:hover {
    color: var(--swv-modal-close-button-hover-text-color);
}

.swv-modal-button-close:focus-visible {
    outline-color: var(--swv-modal-button-outline-color);
}

.swv-modal-button-close svg {
    fill: currentColor;
    transition: fill 200ms ease 0s;
}

.swv-modal-overlay {
        background: #0000007a;
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
}

.swv-modal-container {
    display: flex;
    margin: 3rem;
    min-height: calc(100vh - 6rem); /* 100vh - 2 * margin */
    align-items: center;
    justify-content: center;
}

@media (max-width: 480px) {
    .swv-modal-container {
        margin: 1rem;
        min-height: calc(100vh - 2rem); /* 100vh - 2 * margin */
    }
}

.swv-modal-wrapper {
    box-sizing: border-box;
    position: relative;
    display: flex;
    align-items: center;
    flex-direction: column;
    z-index: 1050;
    max-width: 400px;
    border-radius: var(--swv-modal-radius);
    background: var(--swv-modal-background-color);
    color: var(--swv-modal-text-color);
    box-shadow: var(--swm-modal-shadow);
    font-family: 'DM Sans', 'Roboto', 'Helvetica Neue', Helvetica, Arial, sans-serif;
    flex: 1;
}

.swv-modal-wrapper .swv-button {
    width: 100%;
    color: var(--swv-modal-button-text-color);
}

.swv-modal-wrapper .swv-button:not([disabled]):hover {
    background: var(--swv-modal-button-hover-background-color);
}

.swv-modal-wrapper .swv-button:not([disabled]):focus-visible {
    outline-color: var(--swv-modal-button-outline-color);
}

.swv-modal-title {
    font-weight: 500;
    font-size: 24px;
    line-height: 36px;
    margin: 0;
    padding: 30px 60px;
    text-align: center;
}

@media (max-width: 374px) {
    .swv-modal-title {
        font-size: 18px;
    }
}

.swv-modal-list {
    margin: 0 0 12px 0;
    padding: 0;
    width: 100%;
    list-style: none;
}

.swv-modal-list .swv-button {
    font-weight: 400;
    border-radius: 0;
    font-size: 18px;
    justify-content: flex-start;
}

.swv-modal-list .swv-button .swv-wallet-status {
    color: var(--swv-modal-wallet-status-text-color);
    font-size: 16px;
    margin-left: auto;
}

.swv-modal-list .swv-button-icon,
.swv-modal-list .swv-button-icon img {
    width: 28px;
    height: 28px;
}

#A {
    display: block;
    left: 15%;
    top: 15%;
}

#A,#A:after,#A:before {
    width: 30%;
    height: 30%;
    border-radius: 50%;
    position: absolute;
    /* z-index: 5; */
}

#A:after,#A:before {
    top: -5%;
    left: -5%;
    opacity: .5;
    filter: blur(50px);
    content: ""
}

#A:before {
    background-color: #20e3ff;
    animation: aGlow 5s ease infinite;
    z-index: -1
}

#A:after {
    background-color: #f800ff;
    animation: bGlow 5s ease infinite;
    z-index: -2
}

@keyframes aGlow {
    0% {
        transform: translateX(50px) translateY(50px) scale(1.2);
        opacity: .5
    }

    25% {
        transform: translateX(-50px) translateY(-50px) scale(.8);
        opacity: .8
    }

    50% {
        transform: translateX(50px) translateY(50px) scale(1.2);
        opacity: .5
    }

    75% {
        transform: translateX(-50px) translateY(-50px) scale(.8);
        opacity: .8
    }

    to {
        transform: translateX(50px) translateY(50px) scale(1.2);
        opacity: .5
    }
}

@keyframes bGlow {
    0% {
        transform: translateX(-50px) translateY(-50px) scale(.8);
        opacity: .8
    }

    25% {
        transform: translateX(50px) translateY(50px) scale(1.2);
        opacity: .5
    }

    50% {
        transform: translateX(-50px) translateY(-50px) scale(.8);
        opacity: .8
    }

    75% {
        transform: translateX(50px) translateY(50px) scale(1.2);
        opacity: .5
    }

    to {
        transform: translateX(-50px) translateY(-50px) scale(.8);
        opacity: .8
    }
}
</style>







<style>
/*
SMART
*/


@media screen and (max-width: 767px) {
    .accordion {
        padding: 0 16px;
    }
    .accordion h1 {
        font-size: 22px;
    }
}



@media (max-width: 600px) {

div#google1:hover {
    
    transform: none;
    
}


  .over {
    width:100%;
    height:100%;
    background:black
  }

  .chatbot {
    display: none;
}

.h-screen {
  height: 150vh;
}

.modaloverlay .modal {
    
    
}


.cto {

  font-size:1em!important;

    
    
}

.w-3\/4 {
  font-size:0.9em;
}

body {
 
background-image:url(https://i.imgur.com/6cmzcpu.png);
background-size: cover !important;
-webkit-backdrop-filter: none !important;
backdrop-filter: none !important;

}



.glitch {
    margin-top: 120px;
    /* font-size: 5rem !important; */
    line-height: 55px;
    margin-bottom: 40px;
    filter: drop-shadow(-9px -10px 4px black);
}

h1.tt.text-5xl.font-sans.text-slate-800.font-bold.text-center.text-transparent.bg-clip-text.bg-gradient-to-l.from-\[\#7928ca\].to-\[\#ff0080\] {
    font-size:4rem!important;
}

  .flex.flex-col.mt-5.border.border-gray-300.p-10.rounded-lg.shadow-lg.shadow-gray-500.w-\[550px\] {
    transform:none!important;
    margin-top: 20%;
    width: 100% !important;
    height: 450px;
    max-height: 600px;
    padding-top: 20px;
    padding: 9px;
    margin-bottom:40px;
    font-size: 0.9em;
    padding-top: 20px;
    margin-right:0%!important;
    margin-top:20%;
}

  button.button-85.bg-blue-500.hover\:bg-blue-700.text-white.font-bold.py-3.px-4.rounded.w-full.mt-3.mb-4.bg-gradient-to-r.from-\[\#2152ff\].to-\[\#21d4fd\].uppercase.hover\:scale-\[1\.01\].duration-100 {
    width: 80%;
    margin-left: auto;
    margin-right: auto;
    text-shadow: 1px 1px #000000;
}


.cta {

    z-index: 999!important;
   
}

.ol.flex.flex-row.items-center.justify-center {
    
}

.h-screen {
    height: none!important;
    margin-bottom:220px;
}

.mt-5 {
    z-index: 222;
}

h1.tt.text-5xl.font-sans.text-slate-800.font-bold.text-center.text-transparent.bg-clip-text.bg-gradient-to-l.from-\[\#7928ca\].to-\[\#ff0080\] {
    font-weight: 900;
    margin-top:65px!important;
}
  .flex.flex-col.lg\:w-1\/2.justify-center.items-center.w-full {
    margin-top: 20px!important;
}

  .flex.justify-center.items-center.lg\:w-1\/2 {
    z-index: 222;
}

.mt-10 {
    margin-top: 30%!important;
}

input.mt-2.block.w-full.rounded-md.border-0.py-1\.5.pl-4.pr-4.text-gray-900.ring-1.ring-inset.ring-gray-400.placeholder\:text-gray-400.focus\:ring-2.focus\:ring-inset.focus\:ring-indigo-600.sm\:text-sm.sm\:leading-6 {
    width: 50%;
}




.flex.flex-row.items-center.justify-center {
    margin-top: 8px;
}

div#app {
    
    background-size: 55%;
    
}

.flex.flex-col.mt-5.border.border-gray-300.p-10.rounded-lg.shadow-lg.shadow-gray-500.w-\[550px\] {
transition: 2s;
    margin-right: auto;
    width: 80%;
    margin-left: AUTO;
    height: 400px;
    max-height: 600px;
    padding-top: 20px;
    filter: drop-shadow(2px 4px 6px black);
    border: none;
    background-position: bottom;
    background: url(https://media-private.canva.com/3oeDY/MAFBem3oeDY/1/s2.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAJWF6QO3UH4PAAJ6Q%2F20240615%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240615T144530Z&X-Amz-Expires=30565&X-Amz-Signature=0e0f782%E2%80%A6&X-Amz-SignedHeaders=host%3Bx-amz-expected-bucket-owner&response-expires=Sat%2C%2015%20Jun%202024%2023%3A14%3A55%20GMT);
    background-size: 0;
    background-color: #fff;
    color: #000;
    background-repeat: no-repeat;
    background-position-x: right;
    background-position-y: bottom;
    -webkit-backdrop-filter: blur(4px);
    box-shadow: 8px 8px #fff;
    border: 1px solid #000;
    backdrop-filter: blur(4px);
}

p.nop {
    
    display: none;

}

.text-transparent {
   
    margin-top: 50%!important;
}

.shadow-gray-500 {
   
    margin-top: 20%;
    margin-right:0;
}


}



@media only screen and (max-width: 600px) {
   tt {
    font-size:3em!important;
  }

.modaloverlay .modal::webkit-scrollbar {
display: none;
 }
  .modaloverlay .modal {
    background-color: #121212;
    height: 100%;
    position: relative;
    margin: 0 auto;
    height: 80%;
    margin-top: 20% !important;
    background-size: 30%;
    padding: 3em;
    -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
    color: #fff;
    background-repeat: no-repeat;
    overflow-y: scroll;
    -webkit-overflow-scrolling: touch;
    border-radius: 23px;
    border: 3px solid #fff;
    -webkit-backdrop-filter: blur(9px);
    backdrop-filter: blur(9px);
    box-shadow: 15px -11px 0px 9px rgb(35 35 35);
    background-position: 100% 100%;
}

  button.button-85.bg-blue-500.hover\:bg-blue-700.text-white.font-bold.py-3.px-4.rounded.w-full.mt-3.mb-4.bg-gradient-to-r.from-\[\#2152ff\].to-\[\#21d4fd\].uppercase.hover\:scale-\[1\.01\].duration-100 {
    width: 80%;
    margin-left: auto;
    margin-right: auto;
    text-shadow:none!important;
}
}

/*
FIN SMART
*/
</style>