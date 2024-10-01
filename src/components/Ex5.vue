<template>
  <div>
    <h1>Bài 5</h1>
    <h4>Giới tính: {{ inputValue }}</h4>
    <div>
      <input type="radio" id="Nam" value="Nam" v-model="inputValue" />
      <label for="Nam">Nam</label>
      <input type="radio" id="Nữ" value="Nữ" v-model="inputValue" />
      <label for="Nữ">Nữ</label>
      <input type="radio" id="Khác" value="Khác" v-model="inputValue" />
      <label for="Khác">Khác</label>
    </div>
  </div>
</template>
<script setup >
  import {ref} from "vue"
  const inputValue = ref("")
</script>
<style>
  
</style>