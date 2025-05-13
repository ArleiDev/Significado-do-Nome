<template>
  <div class="min-h-screen from-green-50 to-blue-50 py-12 px-4 sm:px-6 lg:px-8">
    <!-- Form Card -->
    <div class="p-6 max-w-md mx-auto bg-white rounded-xl shadow-md space-y-4 mb-8">
      <h2 class="text-xl font-semibold text-gray-800 text-center">Qual o significado do meu nome?</h2>
      <p class="text-sm text-gray-800 text-center">Software de estudo VueJS e .NET <br>Autor: Arlei J</p>

      <div class="mb-4">
        <label for="nome" class="block text-sm font-medium text-gray-700 mb-2">Digite seu nome:</label>
        <input
          type="text"
          id="nome"
          v-model="nomeLocal"
          class="w-full px-4 py-2 border border-gray-300 rounded-md focus:ring-2 focus:ring-green-500 focus:border-green-500 outline-none transition"
          placeholder="Ex: Maria"
        />
      </div>

      <div class="flex flex-col gap-3">
        <button
          @click="buscarSignificadoPT()"
          :disabled="!nomeLocal"
          class="bg-green-500 text-white px-4 py-2 rounded-lg hover:bg-green-600 transition disabled:opacity-50 disabled:cursor-not-allowed"
        >
          Gerar Significado
        </button>
        
       
      </div>
    </div>

    <!-- Loading and Error States -->
    <div class="max-w-2xl mx-auto">
      <p v-if="carregando" class="text-yellow-600 text-center mb-4">
        <span class="inline-block animate-spin mr-2">⌛</span>
        Buscando significado...
      </p>
      <p v-if="erro" class="text-red-500 text-center mb-4">{{ erro }}</p>
    </div>

    <!-- Result Card -->
    <div v-if="significado" 
         class="max-w-2xl mx-auto transform transition-all duration-300 ease-in-out"
         :class="{'translate-y-0 opacity-100': significado, 'translate-y-4 opacity-0': !significado}">
      <div class="bg-white rounded-xl shadow-lg overflow-hidden">
        <div class="bg-gradient-to-r from-green-400 to-blue-500 px-6 py-4">
          <h3 class="text-xl font-bold text-white">Significado do Nome</h3>
          <p class="text-white opacity-90">{{ nomeLocal }}</p>
        </div>
        <div class="p-6">
          <div class="prose prose-lg">
            <p class="text-gray-700 leading-relaxed whitespace-pre-line">
              {{ significado }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const nomeLocal = ref('')
const significado = ref('')
const carregando = ref(false)
const erro = ref('')

async function buscarSignificadoPT() {
  if (!nomeLocal.value) return
  
  significado.value = ''
  erro.value = ''
  carregando.value = true

  try {
    const response = await fetch(`http://localhost:5282/significadopt/${nomeLocal.value}`)
    const data = await response.json()

    if (response.ok && data) {
      significado.value = data.candidates[0].content.parts[0].text
    } else {
      erro.value = 'Não foi possível obter o significado.'
    }
  } catch (err) {
    erro.value = 'Erro ao conectar com a API.'
  } finally {
    carregando.value = false
  }
}

 
</script>
  