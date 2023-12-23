<script setup lang="ts">
import { ref } from 'vue';
import axios from 'axios';

const CatUrls = ref([]);

async function getCatPic () {
  try {
    const response = await axios.get('https://api.thecatapi.com/v1/images/search?limit=10'); // не получалось зайти на cataas, поэтому взяла другой api, но тоже с котиками
    const urls = response.data.map(item => item.url);
    CatUrls.value.push(...urls);
    console.log(CatUrls.value);
  } catch (error) {
    console.error(error);
  }
}

</script>


<template>
  <div class="container">

    <div class = "chipi-chapa">
      <img src="https://media.tenor.com/fVoHRPRIetUAAAAi/chipi-chipi-chapa-chapa-chipi.gif" alt="chapa1">
    </div>

  <div>
    <h1>Cat Pic</h1>
    <div class="cat-pic" v-for="cats in CatUrls" :key="cats">
      <img :src="cats" alt="cats">
    </div>
    <button @click="getCatPic"> More cats </button>
  </div>

    <div class = "chipi-chapa">
      <img src="https://media.tenor.com/fVoHRPRIetUAAAAi/chipi-chipi-chapa-chapa-chipi.gif" alt="chapa2">
    </div>
  </div>
</template>

<style scoped>


.container
{
  display: flex;
  justify-content: center;
  grid-template-columns: 1fr 9fr 1fr;
}

.chipi-chapa
{
  display: flex;
  width: 250px;
  height: 150px;
  justify-content: center;
  position: sticky;
  top: 20px;
}

.cat-pic
{
  display: flex;
  width: 400px;
  height: 400px;
  justify-content: center;  
  margin: 20px; 
}

.cat-pic img
{
  width: 100%;
  height: 100%;  
}

</style>
