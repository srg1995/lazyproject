<template>
  <ChildComponent ref="percentageComponent" />
  <button @click="banco">añadir cuenta bancaria</button>

  <div>
    <img
      lazy="loading"
      v-lazy="{
        src: lazyOptions.src,
        lifecycle: lazyOptions.lifecycle,
        delay: 500,
      }"
    />
  </div>
</template>

<script setup lang="ts">
import ChildComponent from './ChildComponent.vue'
import { ref, VNode } from 'vue'

const percentageComponent = ref(null)
const banco = () => {
  if (percentageComponent.value) {
    percentageComponent.value.recalculate()
  }
}

const lazyOptions = ref({
  src: 'https://picsum.photos/1280/800',
  lifecycle: {
    loading: (el: VNode) => {
      console.log('cargando imagen', el)
    },
    error: (el: VNode) => {
      console.log('error cargando imagen', el)
    },
    loaded: (el: VNode) => {
      console.log('imagen cargada', el)
    },
  },
})
</script>

<style scoped>
div {
  background-color: white;
  color: red;
}

img[lazy='loading'] {
  background-color: blue;
  width: 520px;
}
</style>
