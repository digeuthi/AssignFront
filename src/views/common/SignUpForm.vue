<template>
    <div>
      <h2>회원가입</h2>
      <form @submit.prevent="handleSubmit">
        <div>
          <label for="name">이름:</label>
          <input type="text" id="name" v-model="name" required />
        </div>
        <div>
          <label for="email">이메일:</label>
          <input type="email" id="email" v-model="email" required />
        </div>
        <div>
          <label for="password">비밀번호:</label>
          <input type="password" id="password" v-model="password" required />
        </div>
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
  
  </style>
  