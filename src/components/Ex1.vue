<template>
  <div>
    <h1>Bài 1</h1>
    <h3>Email</h3>
    <input value="text" v-model="inputValue" />
    <h4>Giá trị: {{ inputValue }}</h4>
  </div>
</template>
<script setup >
  import {ref} from "vue"
  const inputValue = ref("")
</script>
<style>
  
</style>