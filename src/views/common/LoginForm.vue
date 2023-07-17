<template>
    <div>
      <div>
        <h1>로그인</h1>
        <div id="loginForm">
          <form @submit.prevent="fnLogin">
            <p>
              <input class="w3-input" name="uid" placeholder="이메일을 입력하세요" v-model="user_id"><br>
            </p>
            <p>
              <input name="password" class="w3-input" placeholder="비밀번호를 입력하세요" v-model="user_pw" type="password">
            </p>
            <p>
              <button type="submit" class="w3-button w3-green w3-round">Login</button>
            </p>
          </form>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
import axios from 'axios';
import { ref } from 'vue';

const user_id = ref('');
const user_pw = ref('');

const fnLogin = () => {
  if (user_id.value === '') {
    alert('Email을 입력하세요.');
    return;
  }

  if (user_pw.value === '') {
    alert('비밀번호를 입력하세요.');
    return;
  }

  alert('로그인 되었습니다.');
  axios.post('http://localhost:8081/user/sign-in');
};
</script>

  
  <style>
  #loginForm {
    width: 500px;
    margin: auto;
  }
  </style>