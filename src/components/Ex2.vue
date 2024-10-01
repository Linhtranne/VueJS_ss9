<template>
  <div>
    <h1>Bài 2</h1>
    <h3>Màu sắc</h3>
    <input type="color" v-model="inputValue" />
    <h4>Mã màu: {{ inputValue }}</h4>
  </div>
</template>
<script setup >
  import {ref} from "vue"
  const inputValue = ref("")
</script>
<style>
  
</style>