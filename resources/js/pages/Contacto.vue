<template>
  <div class="flex justify-center items-center min-h-screen bg-gray-100 p-4">
    <div class="w-full max-w-3xl bg-white rounded-2xl shadow-lg overflow-hidden flex flex-col">
      <div class="p-12 flex flex-col justify-center">
        <h2 class="text-3xl font-bold mb-6">¿Hablamos?</h2>
        <form @submit.prevent="handleSubmit" class="space-y-4">
          <div>
            <label class="block text-gray-700 font-semibold mb-1" for="name">Nombre</label>
            <input
              v-model="form.name"
              type="text"
              id="name"
              placeholder="Tu nombre"
              class="w-full border border-gray-300 rounded-lg p-3 focus:outline-none focus:ring-2 focus:ring-blue-500"
              required
            />
          </div>
          <div>
            <label class="block text-gray-700 font-semibold mb-1" for="email">Email</label>
            <input
              v-model="form.email"
              type="email"
              id="email"
              placeholder="tu@email.com"
              class="w-full border border-gray-300 rounded-lg p-3 focus:outline-none focus:ring-2 focus:ring-blue-500"
              required
            />
          </div>
          <div>
            <label class="block text-gray-700 font-semibold mb-1" for="subject">Asunto</label>
            <input
              v-model="form.subject"
              type="text"
              id="subject"
              placeholder="Asunto del mensaje"
              class="w-full border border-gray-300 rounded-lg p-3 focus:outline-none focus:ring-2 focus:ring-blue-500"
              required
            />
          </div>
          <div>
            <label class="block text-gray-700 font-semibold mb-1" for="message">Mensaje</label>
            <textarea
              v-model="form.message"
              id="message"
              rows="5"
              placeholder="Escribe tu mensaje..."
              class="w-full border border-gray-300 rounded-lg p-3 focus:outline-none focus:ring-2 focus:ring-blue-500"
              required
            ></textarea>
          </div>
          <button
            type="submit"
            class="bg-blue-500 hover:bg-blue-600 text-white font-semibold py-3 px-6 rounded-lg transition-colors"
          >
            Enviar
          </button>
        </form>
        <p v-if="successMessage" class="mt-4 text-green-600 font-medium">{{ successMessage }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: '',
})

const successMessage = ref('')

const handleSubmit = () => {
  successMessage.value = `Gracias, ${form.name}. Tu mensaje ha sido enviado.`
  form.name = ''
  form.email = ''
  form.subject = ''
  form.message = ''
}
</script>
