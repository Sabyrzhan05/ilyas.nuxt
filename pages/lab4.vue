<template>
    <main class="flex flex-col items-center p-6 bg-white min-h-screen">
      <!-- Заголовок-->
      <div class="w-full max-w-5xl">
        <h1 class="text-3xl font-bold text-[#003366]">Событие матчей</h1>
        <div class="w-full h-0.5 bg-gray-300 my-4"></div>
      </div>
  
      <div class="w-full max-w-5xl flex flex-col lg:flex-row gap-6">
        <!-- Видео -->
        <div class="flex-1">
          <video controls class="w-full rounded-lg border border-[#0055A4]">
            <source src="/video/barys.mp4" type="video/mp4">
            Ваш браузер не поддерживает видео.
          </video>
        </div>
  
        <!-- Панель  -->
        <aside class="w-full lg:w-1/3 p-4 bg-gray-100 rounded-lg border border-gray-300">
          <h2 class="text-lg font-semibold text-[#003366] mb-2">Барыс-Авангард (1:0)</h2>
          <p class="text-gray-700">
            В напряжённом матче "Барыс" одержал победу над соперником со счётом 1:0. 
            Игра прошла на высоких скоростях, а решающий гол был забит в овертайме.
          </p>
        </aside>
      </div>
  
      <!-- Аудио блок  -->
      <div class="w-full max-w-5xl mt-6 p-4 bg-white border border-gray-300 rounded-lg">
      <h2 class="text-xl font-semibold text-[#003366] mb-2">
        Аудио-релиз с Пресс-конференции: После матчевое интервью
      </h2>
      <audio controls class="w-full border border-[#0055A4] p-2 rounded-lg">
        <source src="/audio/barcelona.mp3" type="audio/mp3">
        Ваш браузер не поддерживает аудио.
      </audio>
      </div>
    </main>
  </template>
  
  <style scoped>
  p {
    line-height: 1.5;
  }
  </style>
  