<script setup>
import { ref, computed } from 'vue';
import Inicio from '@/pages/Inicio.vue';
import Experiencia from '@/pages/Experiencia.vue';
import Tecnologias from '@/pages/Tecnologias.vue';
import Blog from '@/pages/Blog.vue';
import Contacto from '@/pages/Contacto.vue';

const currentPage = ref('Inicio')

const menuItems = [
 { name: 'Sobre mi', key: 'Inicio' },
  { name: 'Experiencia', key: 'Experiencia' },
  { name: 'Tecnologías', key: 'Tecnologias' },
  { name: 'Blog', key: 'Blog' },
  { name: 'Contacto', key: 'Contacto' },
]

function setPage(key) {
  currentPage.value = key
}

const currentPageComponent = computed(() => {
  switch (currentPage.value) {
    case 'Inicio': return Inicio
    case 'Experiencia': return Experiencia
    case 'Tecnologias': return Tecnologias
    case 'Blog': return Blog
    case 'Contacto': return Contacto
    default: return Inicio
  }
})
</script>

<template>
  <div class="flex min-h-screen bg-blue-100">
    <nav class="w-60 bg-blue-500 text-white p-6 flex flex-col gap-4 shadow-lg">
      <button
        v-for="item in menuItems"
        :key="item.key"
        @click="setPage(item.key)"
        :class="currentPage === item.key 
          ? 'bg-white text-blue-500 font-semibold rounded-lg py-2 shadow-md' 
          : 'hover:bg-blue-400 rounded-lg py-2 transition'"
      >
        {{ item.name }}
      </button>
    </nav>
    <main class="flex-1 p-8">
      <component :is="currentPageComponent" />
    </main>
  </div>
</template>
