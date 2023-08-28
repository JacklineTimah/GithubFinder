<script setup>
import axios from 'axios';
import { onMounted, ref } from 'vue';
const posts = ref(null);
const followers = ref(null);
const Fullname = ref(null);
const joined= ref(null);
const located= ref(null);
const Bio= ref(null);
const image=ref(null);
const following=ref(null);
const Repositories=ref(null);


onMounted(async () => {
  try {
    const response = await axios.get('https://api.github.com/search/repositories?q=JacklineTimah')
    Fullname.value=response.data.items[0].name;
    joined.value=response.data.items[0].created_at;
    located.value=response.data.items[0].homepage;
    Bio.value=response.data.items[0].avatar_url;
    image.value=response.data.items[0].description;
    following.value=response.data.items[0].owner;
    Repositories.value=response.data.items[0].git_refs_url;
    posts.value = response.data.items[0].followers_url;
    await axios.get(posts.value).then(res=>followers.value=res.data)
  } catch (error) {
    console.error('Error fetching data:',error);
  }
});
console.log(posts);
console.log(followers,"dfgs");
console.log(Fullname,"name");
console.log(joined,"created");
console.log(located,"location");
console.log(Bio,"Profile");
console.log(image,"Image");
console.log(following,"People");
console.log(Repositories,"Repo");
async function getlength(){
return await followers.length

}
console.log(getlength());
</script>
<template>
  <div class="Bio">
  <p1>{{posts}}</p1>
  <p1>{{Fullname}}</p1>
  <p1>{{joined}}</p1>
  <p1>{{located}}</p1>
  <p1>{{Bio}}</p1>
  <p1>{{image}}</p1>
  <p1>{{following}}</p1>
  <p1>{{followers}}</p1>
  <p1>{{Repositories}}</p1>
</div>
</template>


<style scoped>
.Bio{
  padding-top: 10px;
}
.Bio p1{
  color: #FFF;
  font-family: 'Space Mono';
  font-size: 13px;
  font-style: normal;
  font-weight: 400;
  line-height: 25px; 
}
</style>




















































