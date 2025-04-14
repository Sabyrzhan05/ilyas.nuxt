<template>
    <h1>This is protected page. Вы авторизованы </h1>
  </template>
  
  <script setup lang = 'ts'>
  definePageMeta({ middleware: 'sidebase-auth' })
  </script>
  