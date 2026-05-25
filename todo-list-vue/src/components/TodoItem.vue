<script setup>
const props = defineProps({
  tarefa: {
    type: Object,
    required: true
  }
})

const emit = defineEmits(['deletar-tarefa'])

function excluir() {
  emit('deletar-tarefa', props.tarefa.id)
}
</script>

<template>
  <div class="item">
    <span>{{ tarefa.texto }}</span>

    <button @click="excluir">
      Excluir
    </button>
  </div>
</template>

<style scoped>
.item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #f4f4f4;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
}

button {
  background: red;
  color: white;
  border: none;
  padding: 6px 10px;
  cursor: pointer;
}
</style>