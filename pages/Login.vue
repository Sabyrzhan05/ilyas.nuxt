<template>
    <div class="min-h-screen w-full flex items-center justify-center px-4 bg-transparent">
      <div class="bg-[#101820] border-2 border-[#D7A22A] rounded-xl shadow-lg p-10 max-w-md w-full flex flex-col items-center space-y-6">
  
        
        <h1 class="text-3xl font-bold text-white text-center">Welcome</h1>
        <p class="text-sm text-gray-300 text-center">Sign in</p>
  
        
        <button
          @click="signIn('github', { callbackUrl: '/' })"
          class="flex items-center justify-center w-full px-5 py-3 bg-white text-[#0f1620] font-semibold rounded-lg hover:bg-yellow-400 hover:text-black transition duration-300"
        >
          <img src="/images/githu.png" alt="GitHub Logo" class="w-6 h-6 mr-3" />
          Sign in with GitHub
        </button>
  
        <div class="w-full border-t border-[#D7A22A] my-2"></div>
  
        <input
          type="text"
          placeholder="Email/Login"
          class="w-full px-4 py-2 bg-[#0f1620] border border-gray-500 text-white rounded-lg placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-yellow-400"
        />
        <input
          type="password"
          placeholder="Password"
          class="w-full px-4 py-2 bg-[#0f1620] border border-gray-500 text-white rounded-lg placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-yellow-400"
        />
  
        
        <p class="text-xs text-gray-400 text-center pt-2">Eto poka chto demo potom norm sdelaю</p>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  definePageMeta({
    auth: {
      unauthenticatedOnly: true,
      navigateAuthenticatedTo: '/protected',
    },
  })
  
  const { signIn } = useAuth()
  </script>
  