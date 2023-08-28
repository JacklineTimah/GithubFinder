<script setup>
import { ref } from 'vue';
const userData= ref(null);

</script>

<template>
<section v-if="userData">
      <img :src="userData.avatar_url" alt="User Avatar" class="desktop-img">
    <div class="Search">
      <div class="Search-top">
        <img :src="userData.avatar_url" alt="User Avatar" class="mobile-img">
        <div class="Search-top-text">
          <div>
            <h2>{{ userData.name }}</h2>
            <h3>{{ userData.login }}</h3>
            <h2>{{ Username }}</h2>
          </div>
          <div>
            <p>Joined {{ formatDate(userData.created_at) }}</p>
            
          </div>
        </div>
        </div>
    </div>
</section>
</template>
<style scoped>
section{
  display: flex;
  background-color: #1E2A47;
  padding: 32px 24px;
  border-radius: 15px;
  flex-direction: column;
}
.Search{
  display: flex;
  flex-direction: column;
  gap: 23px;
  
}
.Search-top{
  display: flex;
  gap: 20px;
}
.Search-top img{
  border-radius: 70px;
  width: 70px;
  height: 70px;
}
.Search-top-text h2{
color: black;
font-family: 'Space Mono';
font-size: 16px;
font-style: normal;
font-weight: 700;
line-height: normal;
}
.Search-top-text p{
  color: #FFF;
  font-family: 'Space Mono';
  font-size: 13px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}
.Search-top-text h3{
  color: #0079FF;
  font-family: 'Space Mono';
  font-size: 13px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  padding: 6px 0px;
}
@media screen and (min-width: 1000px){
.Search{
    padding: 145px 200px;
  }
  section {
    gap: 37px;
    padding: 48px;
    display: flex;
    flex-direction: row;
  }
  .Search{
    flex: 1;
    padding: 32px 0;
    display: flex;
    flex-direction: column;
    gap: 23px;
    background-color: #1E2A47;
    border-radius: 15px;
  }
  .desktop-img {
    display: block;
    width: 117px;
    height: 117px;
    border-radius: 117px;
    margin-right: 32px;
  }

  .mobile-img {
    display: none;
  }
  .Search-top-text{
    display: flex;
    justify-content: space-between;
    flex: 1;
  }
  .Search-bottom{
    flex-direction: row;
    justify-content: space-between;
  }
  
  button{
    font-size: 16px;
  }
  .search-txt{
    gap: 24px;
  }
  .search-txt img{
    padding-left: 24px;
  }
  input{
    font-size: 18px;
    font-weight: 400;
  }
  .Search-top-text h2{
    font-size: 26px;
    font-weight: 700;
  }
  .Search-top-text h3{
    font-size: 16px;
    font-weight: 400;
  }
  .Search-top-text p{
    font-size: 15px;
    font-weight: 400;
    padding-top: 7px;
  }
}
 </style>

