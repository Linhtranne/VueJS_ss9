<template>
    <div>
      <h1>Bài 3</h1>
      <h4>Ngày sinh: {{ inputValue }}</h4>
      <input type="date" v-model="inputValue" />
    </div>
  </template>
  <script setup >
    import {ref} from "vue"
    const inputValue = ref("")
  </script>
  <style>
    
  </style>