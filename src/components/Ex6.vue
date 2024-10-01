<template>
  <div>
    <h1>Bài 6</h1>
    <h4>Sở thích: {{ inputValue }}</h4>
    <div>
      <input type="checkbox" id="Đá bóng" value="Đá bóng" v-model="inputValue" />
      <label for="Đá bóng">Đá bóng</label>
      <input type="checkbox" id="Bóng chuyền" value="Bóng chuyền" v-model="inputValue" />
      <label for="Bóng chuyền">Bóng chuyền</label>
      <input type="checkbox" id="Bơi Lội" value="Bơi Lội" v-model="inputValue" />
      <label for="Bơi Lội">Bơi Lội</label>
      <input type="checkbox" id="Code" value="Code" v-model="inputValue" />
      <label for="Code">Code</label>
    </div>
  </div>
</template>
<script setup >
  import {ref} from "vue"
  const inputValue = ref([]);
</script>
<style>
  
</style>