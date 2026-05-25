<script setup>
import { ref } from 'vue'

import TodoForm from './components/TodoForm.vue'
import TodoItem from './components/TodoItem.vue'

const tarefas = ref([])

function adicionarTarefa(texto) {
  const textoLimpo = texto.trim()

  if (!textoLimpo) return

  tarefas.value.push({
    id: Date.now(),
    texto: textoLimpo
  })
}

function deletarTarefa(id) {
  tarefas.value = tarefas.value.filter(
    tarefa => tarefa.id !== id
  )
}
</script>

<template>
  <div>
    <h1>Lista de Tarefas</h1>

    <TodoForm
      @add-tarefa="adicionarTarefa"
    />

    <div v-if="tarefas.length === 0">
      <p>Nenhuma tarefa cadastrada.</p>
    </div>

    <ul v-else>
      <TodoItem
        v-for="tarefa in tarefas"
        :key="tarefa.id"
        :tarefa="tarefa"
        @deletar-tarefa="deletarTarefa"
      />
    </ul>
  </div>
</template>