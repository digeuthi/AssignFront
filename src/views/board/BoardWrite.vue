<template>
    <div class="board-detail">
      <h1>게시글 작성</h1>
      <div class="board-contents">
        <input type="text" v-model="title" class="w3-input w3-border" placeholder="제목을 입력해주세요.">
        <input type="text" v-model="author" class="w3-input w3-border" placeholder="작성자를 입력해주세요." v-if="idx === undefined">
      </div>
      <div class="editor-wrapper">
        <textarea v-model="content" class="editor"></textarea>
        <label for="file-upload" class="w3-button w3-round w3-blue-gray file-upload-button">파일 선택</label>
        <input id="file-upload" type="file" @change="handleFileUpload" style="display: none" />
        <img v-if="uploadedImage" :src="uploadedImage" alt="Uploaded Image" />
      </div>
      <div class="board-contents">
        <textarea id="" cols="30" rows="10" v-model="contents" class="w3-input w3-border" style="resize: none;">
        </textarea>
      </div>
      <div class="common-buttons">
        <button type="button" class="w3-button w3-round w3-blue-gray" v-on:click="fnSave">저장</button>&nbsp;
        <button type="button" class="w3-button w3-round w3-gray" v-on:click="fnList">목록</button>
      </div>
    </div>
  </template>
  
  <script setup>
  import router from '@/router';
  import { ref } from 'vue';
  import axios from 'axios';

  const title = ref('');
  const author = ref('');
  const content = ref('');

  const fnSave = () => {

    const article = {
      title : title.value,
      author : author.value,
      content : content.value
    };

    axios.post('http://localhost:8081/board', article)
    .then((response) => {
      console.log(response);
      alert('등록 되었습니다.');
      router.push("./list");
    })
    .catch((error) => {
      console.log(error);
      alert('작성에 실패했습니다.');
    });
  

    const fnList = () => {
      router.push("./list");
    };
  }
  </script>
  <style scoped>
    .h1 {
      text-align: center;
    }
    .board-detail {
      text-align: center;
    }
    .editor-container {
      background-color: #f2f2f2;
      border: 1px solid #ccc;
      padding: 10px;
      text-align: left;
    }

    .ck-editor__editable {
      min-height: 200px;
      padding: 10px;
      border: none;
    }
    .file-upload-wrapper {
      display: flex;
      align-items: center;
      margin-bottom: 10px;
      justify-content: flex-start;
    }

    .file-upload-button {
      margin-left: 10px;
    }
  </style>