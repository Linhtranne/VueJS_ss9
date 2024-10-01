<template>
  <div>
    <h1>Bài 9</h1>
    <div class="form-container">
      <h2>Đăng ký tài khoản</h2>
      <form @submit.prevent="handleSubmit">
        <div class="form-group">
          <label for="name">Tên sinh viên</label>
          <input
            type="text"
            id="name"
            v-model="name"
            placeholder="Nhập tên sinh viên"
            ref="nameInput"
          />
          <span v-if="errors.name" class="error">{{ errors.name }}</span>
        </div>

        <div class="form-group">
          <label for="email">Email</label>
          <input
            type="text"
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

        <div class="form-group">
          <label for="phone">Số điện thoại</label>
          <input
            type="text"
            id="phone"
            v-model="phone"
            placeholder="Số điện thoại"
          />
        </div>

        <button type="submit" class="submit-button">Thêm mới</button>
        <div v-if="successMessage" class="success">{{ successMessage }}</div>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive, nextTick } from "vue";

const name = ref("");
const email = ref("");
const password = ref("");
const phone = ref("");

const successMessage = ref("");

const errors = reactive({
  name: "",
  email: "",
  password: "",
});

const isEmailExist = (email) => {
  const users = JSON.parse(localStorage.getItem("users")) || [];
  return users.some((user) => user.email === email);
};

const handleSubmit = () => {

  errors.name = "";
  errors.email = "";
  errors.password = "";

  if (!name.value) {
    errors.name = "Tên sinh viên không được để trống";
  }
  if (!email.value) {
    errors.email = "Email không được để trống";
  } else if (isEmailExist(email.value)) {
    errors.email = "Email đã tồn tại";
  }
  if (!password.value) {
    errors.password = "Mật khẩu không được để trống";
  }

  if (errors.name || errors.email || errors.password) {
    return;
  }

  const users = JSON.parse(localStorage.getItem("users")) || [];
  users.push({
    name: name.value,
    email: email.value,
    password: password.value,
    phone: phone.value,
  });
  localStorage.setItem("users", JSON.stringify(users));

  successMessage.value = "Đăng ký tài khoản thành công";

  name.value = "";
  email.value = "";
  password.value = "";
  phone.value = "";

  nextTick(() => {
    document.getElementById("name").focus();
  });
};
</script>

<style scoped>
.form-container {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
}

h2 {
  margin-bottom: 16px;
}

.form-group {
  margin-bottom: 12px;
}

label {
  display: block;
  margin-bottom: 4px;
  font-weight: bold;
}

input {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.submit-button {
  background-color: #007bff;
  color: #fff;
  border: none;
  padding: 10px 15px;
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

.success {
  color: green;
  font-size: 14px;
  margin-top: 10px;
}
</style>
