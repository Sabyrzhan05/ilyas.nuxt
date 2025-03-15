<template>
    <main class="flex flex-col items-center justify-center min-h-screen p-6 bg-[#DCF5DC] text-center">
      <div class="flex gap-4 mb-6">
        <label><input class="mx-2" type="radio" value="arn" v-model="selected">Roman Starchenko</label>
        <label><input class="mx-2" type="radio" value="sca" v-model="selected">Anton Burdasov</label>
        <label><input class="mx-2" type="radio" value="oba" v-model="selected">Alikhan Asetov</label>
      </div>
      
      <div class="flex flex-col items-center">
        <div class="blockcap" v-if="selected == 'arn'">
          <img :src="star.image" class="w-60 h-68 pt-2">
          <p class="text-black text-xl">{{ star.name }}</p>
        </div>
        <div class="blockcap" v-if="selected == 'sca'">
          <img :src="burdasov.image" class="w-60 h-68 pt-2">
          <p class="text-black text-xl">{{ burdasov.name }}</p>
        </div>
        <div class="blockcap" v-if="selected == 'oba'">
          <img :src="asetov.image" class="w-60 h-68 pt-2">
          <p class="text-black text-xl">{{ asetov.name }}</p>
        </div>
      </div>
  
      <div class="flex flex-wrap justify-center mt-6 gap-6">
        <div class="blockfor" v-for="(news, index) in blocj" :key="index">
          <img :src="news.image" class="w-60 h-68 pt-2">
          <p class="text-black text-xl">{{ news.name }}</p>
        </div>
      </div>
    </main>
  </template>
  
  <script setup lang="ts">
  import { reactive, ref } from 'vue';
  
  interface full {
    name: string;
    image: string;
  }
  
  const star = reactive<full>({ name: 'Roman Starchenko', image: '/images/star.png' });
  const burdasov = reactive<full>({ name: 'Anton Burdasov', image: '/images/burdasov.png' });
  const asetov = reactive<full>({ name: 'Alikhan Asetov', image: '/images/asetov.png' });
  
  const blocj = reactive<full[]>([
    { name: 'Dinmuhammed Kairzhan', image: '/images/kairzhan.png' },
    { name: 'Kirill Savitskiy', image: '/images/savit.png' },
    { name: 'Batyrlan Muratov', image: '/images/muratov.png' }
  ]);
  
  const selected = ref<string>('');
  </script>
  
  <style scoped>
  .blockcap, .blockfor {
    @apply flex flex-col gap-2 border border-[#0055A4] bg-[#A4C2F4] w-72 h-auto items-center rounded-xl p-4 transition-all duration-300;
  }
  
  .blockcap:hover, .blockfor:hover {
    border-color: #FFD700;
    background-color: #FFEC8B;
  }
  </style>