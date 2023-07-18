<template>
    <div>
      <h1>회원가입</h1>
      <div id="signUpForm">
        <form @submit.prevent="handleSubmit">
          <p>
            <input class="w3-input input-field" name="name" placeholder="이름을 입력하세요" v-model="user_name"><br>
          </p>
          <p>
            <input class="w3-input input-field" name="uid" placeholder="이메일을 입력하세요" v-model="user_id"><br>
          </p>
          <p>
            <input name="password" class="w3-input input-field" placeholder="비밀번호를 입력하세요" v-model="user_pw" type="password">
          </p>
          <p>
            <button type="submit" class="w3-button w3-green w3-round">가입하기</button>
          </p>
        <!-- <label for="name">이름 : </label>  -->
      </form>
      </div>
    </div>
  </template>
  
  <script setup>
  import router from '@/router';
  import axios from 'axios';
  import { ref } from 'vue';
  
  const user_name = ref('');
  const user_id = ref('');
  const user_pw = ref('');
  
  const handleSubmit = () => {
    const user = {
      userName : user_name.value,
      userEmail : user_id.value,
      userPassword : user_pw.value
    };

    axios.post('http://localhost:8081/user/sign-up', user)
    .then((response) => {
      console.log(response);
      alert('회원가입 되었습니다.');
      router.push("/user/sign-in");
    })
    .catch((error) => {
      console.log(error);
      alert('회원가입에 실패했습니다.');
    });
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

input {
  box-align: center;
  width: 300px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-bottom: 10px;
}

input {
    width: 100%;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: inherit;
    margin-bottom: 10px;
  }
  .input-field {
  padding: 8px;
  border: none;
  border-bottom: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 10px;
  width: 500px;
  margin-right: auto;
  margin-left: auto;
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
  