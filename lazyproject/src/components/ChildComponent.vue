<template>
  <h1>Porcentaje completado: {{ percentage }}</h1>
</template>

<script setup lang="ts">
import { ref, onMounted, defineExpose } from 'vue'

const percentage = ref(0)

onMounted(() => {
  percentage.value = 24
})
const recalculate = () => {
  percentage.value = 42
}
defineExpose({ recalculate })
</script>

<style scoped></style>
