<script setup>
import { ref } from 'vue';
import axios from 'axios';

const userData = ref(null);
const username = ref('');
const errorMessage = ref('');

async function getUserData() {
  try {
    
    const response = await axios.get(`https://api.github.com/users/${username.value}`);
    userData.value = response.data;
    console.log(response);
    
  } catch (error) {
    console.error(error);
    errorMessage.value = 'No results'; // Set error message on failure
    userData.value = null;
  }
}

function formatDate(dateString) {
  const options = { day: 'numeric', month: 'short', year: 'numeric' };
  return new Date(dateString).toLocaleDateString('en-US', options);
}
</script>

<template>
  <main>
    
    <div class="container">
    <div>
    <img class="logo" src="../assets/devfinder.svg">
    <div class="content">
    
    <div class="search">
      <div class="search-txt">
      <img src="../assets/Shape 2.svg">
      <input type="text" placeholder="Search GitHub username…">
      </div>
      <div class="errorM">
      <p>{{ errorMessage }}</p>
      <button @click="getUserData">Search</button>
      </div>
    </div>
    
    <section v-if="userData">
      <img :src="userData.avatar_url" alt="User Avatar" class="desktop-img">
    <div class="profile">
      <div class="profile-top">
        <img :src="userData.avatar_url" alt="User Avatar" class="mobile-img">
        <div class="profile-top-text">
          <div>
            <h2>{{ userData.name }}</h2>
            <h3>{{ userData.login }}</h3>
          </div>
          <div>
            <p>Joined {{ formatDate(userData.created_at) }}</p>
          </div>
          
          
        </div>
        <div>

        </div>
        
      </div>
      <div class="bio">
        <p v-if="userData.bio">{{ userData.bio }}</p>
        <p v-else>This profile has no bio</p>
      </div>
      <div class="profile-middle">
        <div class="repos">
          <p>Repos</p>
          <h3>{{ userData.public_repos }}</h3>
        </div>
        <div class="followers">
          <p>Followers</p>
          <h3>{{ userData.followers }}</h3>
        </div>
        <div class="following">
          <p>Following</p>
          <h3>{{ userData.following }}</h3>
        </div>
      </div>

      <div class="profile-bottom">
        <div class="upper-links">
          <div class="location">
          <img src="../assets/003-pin.png">
          <p v-if="userData.location">{{ userData.location }}</p>
          <p v-else class="unavailable">Not available</p>
        </div>
        <div class="link">
          <img src="../assets/002-url.png">
          <p>{{ userData.blog }}</p>
          <p v-if="userData.blog">{{ userData.blog }}</p>
          <p v-else class="unavailable">Not available</p>
        </div>
        </div>
        
        <div class="bottom-links">
          <div class="twitter">
          <img src="../assets/004-twitter.png">
          <p>{{ userData.twitter_username }}</p>
          <p v-if="userData.twitter_username">{{ userData.twitter_username }}</p>
          <p v-else class="unavailable">Not available</p>
        </div>
        <div class="github">
          <img src="../assets/001-office-building.png">
          <p v-if="userData.company">{{ userData.company }}</p>
          <p v-else class="unavailable">Not available</p>
        </div>
        </div>
       
      </div>
      
      
    </div> 
    </section> 
    </div>
    </div>
    </div>
  </main>
</template>

<style scoped>
main{
  background: #141D2F;
}
.desktop-img{
  display: none;
}
.container{
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  
  padding-top: 31px;
  padding-left: 24px;
  padding-right: 24px;
  padding-bottom: 80px;
}
.search{
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-radius: 15px;
  background: #1E2A47;
  
  padding: 7px;
}
.search-txt{
  display: flex;
  align-items: center;
  gap: 7px;
}
button{
  color: #FFF;
  font-family: 'Space Mono';
  font-size: 14px;
  font-style: normal;
  font-weight: 700;
  line-height: normal;
  padding: 12.5px 16px;
  border-radius: 10px;
  background: #0079FF;
  border: none;
}
input{
  color: #FFF;
  font-family: 'Space Mono';
  font-size: 13px;
  font-style: normal;
  font-weight: 400;
  line-height: 25px;
  background-color: #1E2A47;
  border: none;
  width: 100%;
}
.logo{
  padding-bottom: 35px;
}
.errorM{
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
.content{
  display: flex;
  flex-direction: column;
  gap: 16px;
}
section{
  display: flex;
  background-color: #1E2A47;
  padding: 32px 24px;
  border-radius: 15px;
  flex-direction: column;
}
.profile{
  
  display: flex;
  flex-direction: column;
  gap: 23px;
  
}
.profile-top{
  display: flex;
  gap: 20px;
}
.profile-top img{
  border-radius: 70px;
  width: 70px;
  height: 70px;
}
.profile-top-text h2{
  color: #FFF;
  font-family: 'Space Mono';
  font-size: 16px;
  font-style: normal;
  font-weight: 700;
  line-height: normal;
}
.profile-top-text p{
  color: #FFF;
  font-family: 'Space Mono';
  font-size: 13px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}
.profile-top-text h3{
  color: #0079FF;
  font-family: 'Space Mono';
  font-size: 13px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  padding: 6px 0px;
}
.bio{
  padding-top: 10px;
}
.bio p{
  color: #FFF;
  font-family: 'Space Mono';
  font-size: 13px;
  font-style: normal;
  font-weight: 400;
  line-height: 25px; 
}
.profile-middle{
  border-radius: 10px;
  background: #141D2F;
  padding: 18px 15px;
  display: flex;
  justify-content: space-between;

}

.profile-middle p{
  color: #FFF;
  text-align: center;
  font-family: 'Space Mono';
  font-size: 11px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}
.profile-middle h3{
  color: #FFF;
  text-align: center;
  font-family: 'Space Mono';
  font-size: 16px;
  font-style: normal;
  font-weight: 700;
  line-height: normal;
  text-transform: uppercase;
}
.repos, .followers, .following{
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.profile-bottom{
  display: flex;
  flex-direction: column;
  gap: 17px;
}
.profile-bottom p {
  color: #FFF;
  font-family: Space Mono;
  font-size: 13px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}
.location{
  display: flex;
  gap: 25px;
}
.link{
  display: flex;
  gap: 10px;
}
.twitter{
  display: flex;
  gap: 10px;
}
.github{
  display: flex;
  gap: 20px;
}
.unavailable{
  opacity: 0.5;
}
section{
  display: flex;
}
.upper-links, .bottom-links{
  display: flex;
  flex-direction: column;
  gap: 17px;
}



@media screen and (min-width: 1000px) {
  
  .container{
    padding: 145px 200px;
  }

  section {
    gap: 37px;
    padding: 48px;
    display: flex;
    flex-direction: row;
  }

  .profile {
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
  .profile-top-text{
    display: flex;
    justify-content: space-between;
    flex: 1;
  }
  .profile-bottom{
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
  .profile-top-text h2{
    font-size: 26px;
    font-weight: 700;
  }
  .profile-top-text h3{
    font-size: 16px;
    font-weight: 400;
  }
  .profile-top-text p{
    font-size: 15px;
    font-weight: 400;
    padding-top: 7px;
  }
  .bio p{
    font-size: 15px;
  }
  .profile-middle{
    padding: 15px 32px;
  }
  .profile-middle p{
    font-size: 13px;
  }
  .profile-middle h3{
    font-size: 22px;
  }
}
.profile-bottom p{
  font-size: 15px;
}
</style>
