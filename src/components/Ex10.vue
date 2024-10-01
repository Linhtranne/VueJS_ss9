<template>
<div>
  <h1>Bài 10</h1>
  <div class="login-container">
    <h2>Đăng nhập tài khoản</h2>
    <form @submit.prevent="handleSubmit">
      <div class="form-group">
        <label for="email">Email</label>
        <input
          type="email"
          id="email"
          v-model="email"
          placeholder="Nhập email"
        />
        <span v-if="errors.email" class="error">{{ errors.email }}</span>
      </div>

      <div class="form-group">
        <label for="password">Mật khẩu</label>
        <input
          type="password"
          id="password"
          v-model="password"
          placeholder="Nhập mật khẩu"
        />
        <span v-if="errors.password" class="error">{{ errors.password }}</span>
      </div>

      <button type="submit" class="submit-button">Đăng nhập</button>
      <div v-if="message" class="message">{{ message }}</div>
    </form>
  </div>
</div>
</template>

<script setup>
import { ref, reactive } from "vue";

const email = ref("");
const password = ref("");

const message = ref("");

const errors = reactive({
  email: "",
  password: "",
});

const checkLogin = (email, password) => {
  const users = JSON.parse(localStorage.getItem("users")) || [];
  return users.find(user => user.email === email && user.password === password);
};

const handleSubmit = () => {

  errors.email = "";
  errors.password = "";
  message.value = "";

  if (!email.value) {
    errors.email = "Email không được để trống";
  }
  if (!password.value) {
    errors.password = "Mật khẩu không được để trống";
  }

  if (errors.email || errors.password) {
    return;
  }

  const user = checkLogin(email.value, password.value);
  if (user) {
    message.value = "Đăng nhập thành công";
  } else {
    message.value = "Đăng nhập thất bại";
  }
};
</script>

<style scoped>
.login-container {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
  width: 300px;
  margin: 0 auto;
}

h2 {
  text-align: center;
  margin-bottom: 20px;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

input {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.submit-button {
  width: 100%;
  background-color: #007bff;
  color: #fff;
  border: none;
  padding: 10px;
  cursor: pointer;
  border-radius: 4px;
  font-size: 16px;
}

.submit-button:hover {
  background-color: #0056b3;
}

.error {
  color: red;
  font-size: 12px;
}

.message {
  margin-top: 10px;
  font-size: 14px;
  color: green;
  text-align: center;
}
</style>
