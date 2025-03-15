<template>
  <header class="flex flex-row w-full relative bg-[#101820] border-b-2 border-[#D7A22A] max-sm:justify-between max-sm:z-10 max-sm:relative">
  <div class="basis-1/4 flex items-center justify-start px-8 min-w-40 max-sm:basis-auto">
    <img src="public/images/Logo.png" class="w-16 h-16 bg-transparent" alt="Team Logo">
  </div>
  <div class="basis-1/4 max-sm:hidden"></div>

  <nav
    :class= "{
      'basis-1/2 flex flex-row items-center justify-end px-8 gap-4 font-anton': !burger || burger, 'max-sm:basis-auto max-sm:absolute max-sm:top-full max-sm:w-full max-sm:justify-center max-sm:flex-col max-sm:gap-2 max-sm:bg-[#101820] max-sm:px-2 max-sm:z-0': burger,
      'max-sm:hidden': !burger}">
    <NuxtLink to="/" class="my-auto p-2 text-white hover:bg-[#D7A22A] hover:text-black max-sm:w-full max-sm:border-b-2 max-sm:border-[#D7A22A] max-sm:text-center">Home</NuxtLink>
    <div class="my-auto p-2 text-white hover:bg-[#D7A22A] hover:text-black max-sm:w-full max-sm:text-center max-sm:px-0 max-sm:pb-0" @click="switch_submenu">Labs
      <div class="flex flex-col absolute top-full bg-[#101820] text-white w-56 text-center max-sm:relative max-sm:w-full max-sm:bg-[#D7A22A] max-sm:text-black" v-show="submenu">
        <NuxtLink to="/lab3" class="my-auto p-2 border-b-2 border-[#D7A22A] hover:bg-[#D7A22A] hover:text-black max-sm:w-full max-sm:border-t-2 max-sm:text-center">Lab3</NuxtLink>
        <NuxtLink to="/lab4" class="my-auto p-2 border-b-2 border-[#D7A22A] hover:bg-[#D7A22A] hover:text-black max-sm:w-full max-sm:text-center">Lab4</NuxtLink>
        <NuxtLink to="/lab5" class="my-auto p-2 border-b-2 border-[#D7A22A] hover:bg-[#D7A22A] hover:text-black max-sm:w-full max-sm:text-center">Lab5</NuxtLink>
        <NuxtLink to="/lab6" class="my-auto p-2 border-b-2 border-[#D7A22A] hover:bg-[#D7A22A] hover:text-black max-sm:w-full max-sm:text-center">Lab6</NuxtLink>
      </div>
    </div>

    <NuxtLink to="/login" class="my-auto p-2 text-white hover:bg-[#D7A22A] hover:text-black max-sm:w-full max-sm:text-center">Login</NuxtLink>
    <NuxtLink to="/logout" class="my-auto p-2 text-white hover:bg-[#D7A22A] hover:text-black max-sm:w-full max-sm:text-center">Logout</NuxtLink>
  </nav>

    <div v-if="!burger" @click="switch_burger" class="max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6 max-sm:mt-5">
        <span class="h-[3px] w-full bg-blue-950"></span>
        <span class="h-[3px] w-full bg-blue-950"></span>
        <span class="h-[3px] w-full bg-blue-950"></span>
        
    </div>

    <div v-else @click="switch_burger" class="max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6 max-sm:mt-5">
        <span class="h-[3px] w-full bg-blue-950 rotate-45 relative top-[9px]"></span>
        <span class="h-[3px] w-full bg-blue-950 opacity-0"></span>
        <span class="h-[3px] w-full bg-blue-950 relative bottom-3 rotate-[-45deg]"></span>
        
    </div>
</header>

  <main class="p-5 flex bg-green-100 min-h-screen">
    <slot />
  </main>
  <footer class="flex flex-row w-full bg-[#101820] border-t-2 border-[#D7A22A] items-center justify-center px-4 py-2 gap-4">
    <a href="https://www.youtube.com"><img src="public/images/youtube.png" class="w-16 h-16"></a>
    <a href="https://github.com"><img src="public/images/hub.png" class="w-16 h-16"></a>
    <a href="https://www.facebook.com"><img src="public/images/fc.png" class="w-16 h-16 bg-transparent"></a>
</footer>
</template>


<script setup lang="ts">
import { useHead } from '#app'
import {ref} from 'vue'

useHead({
  script: [
    {
      async: true,
      src: 'https://www.googletagmanager.com/gtag/js?id=G-5994T6MV4H',
    },
    {
      innerHTML: `
        window.dataLayer = window.dataLayer || [];
        function gtag(){ dataLayer.push(arguments); }
        gtag('js', new Date());
        gtag('config', 'G-5994T6MV4H');
      `,
      type: 'text/javascript',
    },
   ],
   __dangerouslyDisableSanitizersByTagID: {
    gtag: ['innerHTML']
   },
});

const burger = ref<boolean>(false)
const submenu = ref<boolean>(false)
const switch_burger = ()=> {burger.value = !burger.value}
const switch_submenu = ()=> {submenu.value = !submenu.value}

</script>


