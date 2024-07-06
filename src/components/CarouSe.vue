<template>
  


    

    <div class="section full-height over-hide px-4 px-sm-0">
        <div class="container">
            <div class="row full-height justify-content-center">
                <div class="col-lg-10 col-xl-8 align-self-center padding-tb">
                    <div class="section mx-auto text-center slider-height-padding">
                        <input class="checkbox frst" type="radio" id="slide-1" name="slider" checked/>
                        <label for="slide-1"></label>
                        <input class="checkbox scnd" type="radio" name="slider" id="slider-2"/>
                        <label for="slider-2"></label>
                        <input class="checkbox thrd" type="radio" name="slider" id="slider-3"/>
                        <label for="slider-3"></label>
                        <input class="checkbox foth" type="radio" name="slider" id="slider-4"/>
                        <label for="slider-4"></label>
                        <ul>
                            <li >
                            
                                <a href="#google1"><span>CREATE TOKEN</span></a>
                            </li>

                            
                            <li>
                            <a href="#google2">
                                <span>MINT NFT</span>
                                   </a>
                            </li>
                         
                            <li>
                                <span>SOLANA CASINO</span>
                            </li>
                            <li>
                                <span>SKATEBOARD FACE</span>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

</script>

<style scoped>



/* Please ❤ this if you like it! */


/* ========================================= * 
                BEST VIEWED FULLSCREEN
   https://codepen.io/ig_design/full/NWxwBvw
 * ========================================= */
@import url('https://fonts.googleapis.com/css?family=Poppins:400,500,600,700,800,900');

body{
    font-family: 'Poppins', sans-serif;
    font-weight: 300;
    font-size: 15px;
    line-height: 1.7;
    color: #343434;
    background-color: #f1f2f6;
    overflow-x: hidden;
}
a {
    cursor: pointer;
}
a:hover {
    text-decoration: none;
}

.section{
  position: relative;
  width: 80%;
  display: block;
}
.full-height{
  
}
.over-hide{
  overflow: hidden;
}
.padding-tb{
  padding: 100px 0;
}
[type="radio"]:checked,
[type="radio"]:not(:checked){
  position: absolute;
  left: -9999px;
}
.checkbox:checked + label,
.checkbox:not(:checked) + label{
  position: relative;
  cursor: pointer;
  margin: 0 auto;
  text-align: center;
  margin-right: 1em;
    margin-left: 1em;
  display: inline-block;
  width: 50px;
  height: 50px;
  background-size: cover;
  background-position: center;
  box-sizing: border-box;
  -webkit-transition: all 0.2s ease;
  transition: all 0.2s ease;
  background-image: url('https://i.imgur.com/miErJ5i.png');
  animation: border-transform 6s linear infinite alternate forwards;
    -webkit-animation-play-state: paused;
    -moz-animation-play-state: paused;
    animation-play-state: paused;
    filter:drop-shadow (2px 2px black);
}
.checkbox.scnd + label{
  background-image: url('https://i.imgur.com/4AHHNBn.png');
}
.checkbox.thrd + label{
  background-image: url('https://i.imgur.com/MEadbgt.png');
}
.checkbox.foth + label{
  background-image: url('https://assets.codepen.io/1462889/sl4.jpg');
}

.checkbox:checked + label{
  box-shadow: 0 8px 25px 0 rgba(16,39,112,.3);
  transform: scale(1.3);
    -webkit-animation-play-state: running;
    -moz-animation-play-state: running;
    animation-play-state: running;
    opacity:0.5;
}
@keyframes border-transform{
  0%,100% { border-radius: 63% 37% 54% 46% / 55% 48% 52% 45%; } 
  14% { border-radius: 40% 60% 54% 46% / 49% 60% 40% 51%; } 
  28% { border-radius: 54% 46% 38% 62% / 49% 70% 30% 51%; } 
  42% { border-radius: 61% 39% 55% 45% / 61% 38% 62% 39%; } 
  56% { border-radius: 61% 39% 67% 33% / 70% 50% 50% 30%; } 
  70% { border-radius: 50% 50% 34% 66% / 56% 68% 32% 44%; } 
  84% { border-radius: 46% 54% 50% 50% / 35% 61% 39% 65%; } 
}

.slider-height-padding {
  padding-top: 440px;
}

ul {
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  width: 100%;
  z-index: 100;
  padding: 0;
  margin: 0;
  list-style: none;
}
ul li {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  display: block;
  z-index: 100;
  padding: 0;
  transition:2s;
  margin: 0;
  list-style: none;
  height: 400px;
  filter:drop-shadow(2px 4px 6px black);
  background-size: cover;
  background-position: center;
  background-image: url('https://i.imgur.com/miErJ5i.png');
  border-radius: 50%;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
  font-weight: 900;
  font-size: 16px;
  letter-spacing: 2px;
  line-height: 2.7;
  color: #343434;
  writing-mode: vertical-rl;
  opacity: 0;
  pointer-events: none;
box-shadow: 0 8px 25px 0 rgb(0 0 0);
  -webkit-transition: all 0.5s ease;
  transition: all 0.5s ease;
}
ul li span {
  font-size: 2em;
    font-weight: 900;
    font-family: Sora;
    color: #fff;
    text-shadow: 5px 5px 5px #000;
    line-height: 10px;
}
ul li:nth-child(2) {
  background-image: url('https://i.imgur.com/4AHHNBn.png');
}
ul li:nth-child(3) {
  background-image: url('https://i.imgur.com/MEadbgt.png');
}
ul li:nth-child(4) {
  background-image: url('https://assets.codepen.io/1462889/sl4.jpg');
}


.checkbox.frst:checked ~ ul li:nth-child(1) {
  opacity: 1;
  pointer-events: auto;
  border-radius: 16px;
}
.checkbox.scnd:checked ~ ul li:nth-child(2) {
  opacity: 1;
  pointer-events: auto;
  border-radius: 16px;
}
.checkbox.thrd:checked ~ ul li:nth-child(3) {
  opacity: 1;
  pointer-events: auto;
  border-radius: 16px;
}
.checkbox.foth:checked ~ ul li:nth-child(4) {
  opacity: 1;
  pointer-events: auto;
  border-radius: 16px;
}

li:hover {
    transition: 1s;
    transform: scale(0.95);
}

.logo {
    position: absolute;
    top: 30px;
    right: 30px;
    display: block;
    z-index: 100;
    transition: all 250ms linear;
}
.logo img {
    height: 26px;
    width: auto;
    display: block;
}



@media (max-width: 767px) {
  .slider-height-padding {
    padding-top: 340px;
  }
  ul li {
    height: 300px;
    font-size: 13px;
    letter-spacing: 1px;
  }
}

@media (max-width: 575px) {
  .slider-height-padding {
    padding-top: 240px;
  }
  .section {
    width:100%!important;
  }
  ul li {
    height: 200px;
  }
}

</style>
