<template>
  <div>
    <h1>Bài 8</h1>
    <div class="form-container">
      <h2>Thêm mới tài khoản</h2>
      <form @submit.prevent="handleSubmit">
        <div class="form-group">
          <label for="name">Tên sinh viên</label>
          <input
            type="text"
            id="name"
            v-model="student.name"
            placeholder="Nhập tên sinh viên"
          />
        </div>
  
        <div class="form-group">
          <label for="email">Email</label>
          <input
            type="text"
            id="email"
            v-model="student.email"
            placeholder="Nhập email"
          />
        </div>
  
        <div class="form-group">
          <label for="password">Mật khẩu</label>
          <input
            type="password"
            id="password"
            v-model="student.password"
            placeholder="Nhập mật khẩu"
          />
        </div>

        <div class="form-group">
          <label for="reassword">Nhập lại mật khẩu</label>
          <input
            type="password"
            id="repassword"
            v-model="repassword"
            placeholder="Nhập lại mật khẩu"
          />
        </div>
  

  
        <button type="submit" class="submit-button">Thêm mới</button>
      </form>
    </div>
  </div>
  </template>
  
  <script>
export default {
  data() {
    return {
      student: {
        name: '',
        email: '',
        password:'',
      }
    };
  },
  methods: {
    handleSubmit() {
      console.log('Dữ liệu sinh viên:', this.student);
        this.student = {
        name: '',
        email: '',
        password: '',
      };
    }
  }
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
  
  input, select {
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
  </style>
  