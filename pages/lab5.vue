<template>
    <main class="bg-[#e6fff0] py-12 px-4 min-h-screen flex flex-col items-center justify-start">
      <div class="w-full bg-white shadow-xl rounded-xl p-8">
        <h1 class="text-3xl font-bold text-[#003366] mb-10 text-center border-b pb-4">
          Интерактивный раздел
        </h1>
  
        <section class="mb-12">
          <h2 class="text-2xl font-semibold mb-4 text-[#003366]">Обзор на видео-матчи</h2>
  
          <label for="select" class="block mb-2 font-medium">Выберите видео:</label>
          <select id="select" v-model="selectus" class="p-2 rounded border w-full max-w-xs">
            <option value="bar">14.03.2025</option>
            <option value="ani">12.03.2025</option>
            <option value="hat">10.03.2025</option>
            <option value="pod">08.03.2025</option>
          </select>
  
          <div class="mt-6">
            <div v-if="selectus === 'bar'">
              <barysgame1 />
            </div>
            <div v-else-if="selectus === 'ani'">
              <barysgame2 />
            </div>
            <div v-else-if="selectus === 'hat'">
              <Barysgame3 />
            </div>
            <div v-else-if="selectus === 'pod'">
              <Barysgame4 />
            </div>
          </div>
        </section>
  
        <section class="mb-12">
          <h2 class="text-2xl font-semibold mb-4 text-[#003366]">Поиск игрока по фамилии</h2>
  
          <input
            name="filter"
            v-model="search"
            placeholder="input"
            class="p-2 rounded border w-full max-w-xs"
          />
          <div v-for="(image, index) in finder" :key="index" class="mt-4">
            <img :src="image.image" class="w-60 rounded shadow border" />
          </div>
        </section>
  
        <section class="text-center">
          <h2 class="text-2xl font-semibold mb-6 text-[#003366]">Calculator</h2>
  
          <form class="flex flex-wrap justify-center gap-6">
            <div class="flex flex-col">
              <label for="fst">First number:</label>
              <input name="fst" type="number" v-model="first" class="p-2 border rounded w-32 text-center" />
            </div>
            <div class="flex flex-col">
              <label for="snd">Second number:</label>
              <input name="snd" type="number" v-model="second" class="p-2 border rounded w-32 text-center" />
            </div>
          </form>
  
          <div class="flex gap-4 mt-6 flex-wrap justify-center">
            <button @click="set_op('+')" class="calc-btn bg-[#003366]">+</button>
            <button @click="set_op('-')" class="calc-btn bg-[#FFD700] text-black">−</button>
            <button @click="set_op('*')" class="calc-btn bg-[#003366]">*</button>
            <button @click="set_op('/')" class="calc-btn bg-[#FFD700] text-black">÷</button>
          </div>
  
          <div class="text-2xl mt-6 font-bold text-[#003366]">Your result is: {{ calc }}</div>
        </section>
  
      </div>
    </main>
  </template>
  
  <script setup lang="ts">
  import { ref, computed, reactive } from "vue"
  
  const selectus = ref<string>('bar')
  const search = ref<string>('Asetov')
  
  interface stking {
    name: string
    image: string
  }
  
  const filtering = reactive<stking[]>([
    { name: 'Asetov', image: "/images/asetov.png" },
    { name: 'Burdasov', image: "/images/burdasov.png" },
    { name: 'Kairzhan', image: "/images/kairzhan.png" },
    { name: 'Muratov', image: "/images/muratov.png" },
    { name: 'Savitskiy', image: "/images/savit.png" },
    { name: 'Starchenko', image: "/images/star.png" },
  ])
  
  const finder = computed(() => {
    return filtering.filter(img =>
      img.name.toLowerCase().includes(search.value.toLowerCase())
    )
  })
  
  const first = ref<number>(0)
  const second = ref<number>(0)
  const signn = ref<string>('')
  
  function set_op(op: string) {
    signn.value = op
  }
  
  const calc = computed((): number => {
    switch (signn.value) {
      case "*": return first.value * second.value
      case "/":
        try {
          return parseFloat((first.value / second.value).toFixed(1))
        } catch {
          return 0
        }
      case "+": return first.value + second.value
      case "-": return first.value - second.value
      default: return 0
    }
  })
  </script>
  
  <style scoped>
  .calc-btn {
    @apply text-white px-4 py-2 rounded-xl hover:bg-opacity-80 border-2 border-black w-16 text-lg font-bold;
  }
  </style>
  