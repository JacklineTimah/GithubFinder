<script setup>
import ThedescriptionVue from './Thedescription.vue';
import TheSearchComponent from './TheSearchComponent.vue';
</script>

<template>
  <main>
    <div class="Group10">
      <div class="bar">
    <div class="DevFinder"><h2>DevFinder</h2></div>
    <!--img class="moon" src="src/assets/moon.png" alt="Moon"--><h3>DARK</h3>
  </div>
  <div class="Git">
    <div class="Type">
      <div class="Type-txt">
      <img src="src/assets/Shape 2.png" alt="Search">
      <input type="text" placeholder="Search GitHub username…">
      <button>Search</button>
      </div>
      </div>
    </div>
  </div> 
  </main>
  <ThedescriptionVue />
  <TheSearchComponent />
</template>

<style scoped>
main{
  background: white;
}
.Group10{
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  padding-top: 31px;
  padding-left: 24px;
  padding-right: 24px;
  padding-bottom: 80px;
  background-color: #FFF;
}
.Type{
  width: 573px;
  height: 69px;
  background:#FEFEFE; 
  box-shadow: '0px 16px 30px -10px rgba(70.32, 96.33, 187.38, 0.20)';
  border-radius: 15px;
  padding-top: 36px;
}
.Type-txt{
  display: flex;
  align-items: center;
  gap: 7px;
}
h3{
text-align: right;
color:#4B6A9B;
font-size:13px; 
font-family: monospace;
font-weight:700;
letter-spacing: 2.50px;
word-wrap: break-word;
}
.Git{
  display: flex;
  flex-direction: column;
  gap: 16px;
}
button{
  color: #FFF;
  font-family: 'Space Mono';
  font-size: 14px;
  font-style: normal;
  font-weight: 700;
  line-height: normal;
  padding: 12.5px;
  border-radius: 10px;
  background: #0079FF;
  border: none;
  height: 69px;
}
input{
  color: #FFF;
  font-family: monospace;
  font-size: 13px;
  font-style: normal;
  font-weight: 400;
  line-height: 25px;
  background-color: white;
  border: none;
  width: 573px;
  height: 69px;
  
}
.DevFinder{
color:#222731;
font-size: 26; 
font-family:monospace;
font-Weight:700; 
word-wrap:break-word;
}
.invalid{
  display: flex;
  align-items: center;
  gap: 20px;
  color: #F74646;
  font-family: 'Space Mono';
  font-size: 14px;
  font-style: normal;
  font-weight: 700;
  line-height: normal;
}
.bar{
width: 573px;
 height: 38px;
 justify-content:center;
 align-items:center;
 gap:367px; 
 display:inline-flex;
}

.moon{
  width:20px;
  height: 20px;
  padding-right: 98px;
}
</style>





































<!--style scoped>
.Group10{
    width: 573px;
    height: 38px;
    justify-content: center; 
    align-items:center ; 
    gap: 367px; 
    display: inline-flex;
    padding-left: 97px;
    padding-right: 98px;
    margin-top: 144px;
    margin-left: 97px;
    margin-right:98px ;
 }
 .DevFinder h1{
    color:#222731;
    font-size: 26px;
    font-family:monospace; 
    font-weight: 600;
    word-wrap: break-word;
 }
 .DarkandMoon{
    max-width:78px;
    max-height: 20px; 
    padding-left: 2px;
    justify-content: center;
    align-items:flex-start;
    gap: 16px;
    display: inline-flex;
 }
 .dark{
   text-align: left; 
   color: #4B6A9B;
   font-size: 13px;
   font-family: monospace;
   font-weight: 700;
   letter-spacing: 2.50;
   word-wrap: break-word;
 }
 .Moon{
    width: 20px;
    height: 20px;
    background-color:#4B6A9B ;
 }






 @media screen and( max-width:1024px;){

 }*/
</style-->