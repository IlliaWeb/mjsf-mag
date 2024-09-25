<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <h1>
      Інженерія програмного забезпечення 2 курс 8.1213, Тюшняков Ілля Сергійович
    </h1>
  </div>

</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
