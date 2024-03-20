
<script setup lang="ts">

import { ref } from 'vue';
// Définition du type pour les URL d'images
type ImageUrl = string;

// Définition du type pour le tableau certifs

const showModal = ref(false);
const selectedImage = ref<string>('');
 const certifs = ref<string[]>([
    'js-beginner.png',
    'js-beginner.png',
    'js-front-intermediaire.png',
    'js-inter.png',
    'node-inter.png',
    'node-js-beginner.png',
    'vue-beginner.png',
    'web-api.png'
])

function openModal(image: ImageUrl) {
  selectedImage.value = `https://github.com/AndrianD/certifications/blob/main/${image}?raw=true&auto=format&q=75&fit=crop&w=600`;
  showModal.value = true;
}

function closeModal() {
  showModal.value = false;
}

</script>
<template>
  <div class="bg-white dark:bg-gray-800 h-screen h-full py-6 sm:py-8 lg:py-12">
    <div class="mx-auto max-w-screen-2xl px-4 md:px-8">
        <div class="mb-4 flex items-center justify-between gap-8 sm:mb-8 md:mb-12">
            <div class="flex items-center gap-12">
                <h2 class="text-2xl font-bold text-gray-800 lg:text-3xl dark:text-white">Certifications</h2>

                <p class="hidden max-w-screen-sm text-gray-500 dark:text-gray-300 md:block">
                    This is a section of some simple filler text,
                    also known as placeholder text. It shares some characteristics of a real written text.
                </p>
            </div>
        </div>

        <div 
        class="grid grid-cols-2 gap-4 sm:grid-cols-3 md:gap-6 xl:gap-8"
        >
            <!-- image - start -->
            <a href="#"  v-for="img,index in certifs" :key="index"
                class="group relative flex h-48 items-end overflow-hidden rounded-lg bg-gray-100 shadow-lg md:h-80" @click="openModal(img)">
                <img :src="`https://github.com/AndrianD/certifications/blob/main/${img}?raw=true&auto=format&q=75&fit=crop&w=600`" loading="lazy" alt="Photo by Minh Pham" class="absolute inset-0 h-full w-full object-cover object-center transition duration-200 group-hover:scale-110" />

                <div
                    class="pointer-events-none absolute inset-0 bg-gradient-to-t from-gray-800 via-transparent to-transparent opacity-50">
                </div>
            </a>
            <!-- image - end -->

        </div>
    </div>
</div>

  <!-- Modal -->
  <div v-if="showModal" class="fixed inset-0 z-10 flex items-center justify-center bg-gray-900 bg-opacity-50">
    <div class="bg-white p-6 rounded-lg shadow-xl">
        
        <div @click="closeModal" class="absolute top-4 right-4 w-8 h-8 flex items-center justify-center rounded-full bg-gray-200 hover:bg-gray-300 cursor-pointer">
        <svg class="w-6 h-6 text-gray-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
        </svg>
      </div>
      <!-- Contenu de la modal -->
      <img :src="selectedImage" alt="Modal Image" class="max-w-full max-h-full" @click="closeModal">
    </div>
  </div>

</template>
