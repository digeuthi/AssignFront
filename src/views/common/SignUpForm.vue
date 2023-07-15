<template>
    <div>
      <h1>회원가입</h1>
      <form @submit.prevent="handleSubmit">
        <p>
          <label for="name">이름:</label>
          <input type="text" id="name" v-model="name" required />
        </p>
        <p>
          <label for="email">이메일:</label>
          <input type="email" id="email" v-model="email" required />
        </p>
        <p>
          <label for="password">비밀번호:</label>
          <input type="password" id="password" v-model="password" required />
        </p>
        <div>
          <button type="submit" class="w3-button w3-green w3-round">가입하기</button>
        </div>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        email: '',
        password: '',
        name: '',
      };
    },
    methods: {
      handleSubmit() {
        // 회원가입 로직 구현
        const userData = {
          email: this.email,
          password: this.password,
          name: this.name,
        };
        console.log(userData);
      },
    },
  };
  </script>
  
  <style scoped>
#signupForm {
    width: 500px;
    margin: auto;
  }
.signup-form {
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f2f2f2;
  border: 1px solid #ccc;
}

.signup-form label {
  display: block;
  margin-bottom: 10px;
}

.signup-form input[type="text"],
.signup-form input[type="email"],
.signup-form input[type="password"] {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-bottom: 10px;
}

.signup-form button {
  width: 100%;
  padding: 10px;
  background-color: #4caf50;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
  
  </style>
  