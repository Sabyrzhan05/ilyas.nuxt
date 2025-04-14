<template>
  <div>
    <h1>Home page</h1>
  </div>

</template>

<script setup lang = 'ts'>
definePageMeta({
auth: {
  unauthenticatedOnly: false,
  navigateAuthenticatedTo: '/protected',
},
})

// const {data} = await useFetch('/api/me')
</script>
