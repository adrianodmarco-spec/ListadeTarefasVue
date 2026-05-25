<script setup>
import { ref } from 'vue'

const emit = defineEmits([
  'add-tarefa'
])

const novaTarefa = ref('')
const erro = ref('')

function enviarFormulario() {
  const texto = novaTarefa.value.trim()

  if (!texto) {
    erro.value = 'Digite uma tarefa válida.'
    return
  }

  emit('add-tarefa', texto)

  novaTarefa.value = ''
  erro.value = ''
}
</script>

<template>
  <form @submit.prevent="enviarFormulario">
    <input
      v-model="novaTarefa"
      type="text"
      placeholder="Digite uma tarefa"
    />

    <button type="submit">
      Adicionar
    </button>

    <p v-if="erro">
      {{ erro }}
    </p>
  </form>
</template>