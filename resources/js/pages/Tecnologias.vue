<template>
  <div class="flex justify-center items-center min-h-screen bg-gray-100 p-4">
    <div class="w-full max-w-5xl bg-white rounded-2xl shadow-lg overflow-hidden flex flex-col">
      <div class="p-12 flex flex-col justify-center">
        <h2 class="text-2xl font-semibold mb-6">Tecnologías utilizadas</h2>
        <div class="space-y-4">
          <div v-for="tech in technologies" :key="tech.name">
            <div class="flex justify-between mb-1">
              <span class="font-semibold text-gray-700">{{ tech.name }}</span>
              <span class="font-medium text-gray-600">{{ tech.level }}%</span>
            </div>
            <div class="w-full bg-gray-300 rounded-full h-4 overflow-hidden">
              <div
                class="bg-blue-500 h-4 rounded-full transition-all duration-1000"
                :style="{ width: tech.level + '%' }"
              ></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const technologies = ref([
  { name: 'Java', level: 70 },
  { name: 'JavaScript', level: 80 },
  { name: 'PHP', level: 75 },
  { name: 'Python', level: 60 },
  { name: 'CSS', level: 85 },
  { name: 'Laravel', level: 70 },
  { name: 'Vue', level: 65 },
])
</script>
