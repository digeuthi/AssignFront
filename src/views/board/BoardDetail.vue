<template>
    <div class="board-detail">
      <div class="common-buttons">
        <button type="button" class="w3-button w3-round w3-blue-gray" v-on:click="fnUpdate">수정</button>&nbsp;
        <button type="button" class="w3-button w3-round w3-red" v-on:click="fnDelete">삭제</button>&nbsp;
        <button type="button" class="w3-button w3-round w3-gray" v-on:click="fnList">목록</button>
      </div>
      <div class="board-contents">
        <h3>{{ title }}</h3>
        <div>
          <strong class="w3-large">{{ author }}</strong>
          <br>
          <span>{{ created_at }}</span>
        </div>
      </div>
      <div class="board-contents">
        <span>{{ contents }}</span>
      </div>
      <div class="common-buttons">
        <button type="button" class="w3-button w3-round w3-blue-gray" v-on:click="fnUpdate">수정</button>&nbsp;
        <button type="button" class="w3-button w3-round w3-red" v-on:click="fnDelete">삭제</button>&nbsp;
        <button type="button" class="w3-button w3-round w3-gray" v-on:click="fnList">목록</button>
      </div>
    </div>
  </template>
  
  <script setup>

  import { ref } from 'vue';
  import router from '@/router';
  import axios from 'axios';

  const title = ref('');
  const author = ref('');
  const contents = ref('');
  const created_at = ref('');


  const fnUpdate = () => {

    const article = {
      title : title.value,
      author : author.value,
      contents : contents.value
    };

    axios.patch('http://localhost:8081/board', article)
    .then((response) => {
      console.log(response);
      alert('수정 되었습니다.');
      router.push("./list");
    })
    .catch((err) => {
      console.log(err);
      alert('수정에 실패했습니다.');
    });
  };

  const fnList = () => {
      router.push({ name: 'boardList' });
  };

  const fnDelete = () => {
    if (!confirm("삭제하시겠습니까?")) return;

    axios.delete('http://localhost:8081/board/{boardNumber}', {}).then(() => {
      alert('삭제되었습니다');
    fnList();
    }).catch((err) => {
    console.log(err);
  });

  };
  
  </script>

  <style scoped>
  
  
  </style>