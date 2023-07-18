<template>
    <div class="board-list">
      <h1>게시글 목록</h1>
      <div class="common-buttons">
        <button type="button" class="w3-button w3-round w3-blue-gray" v-on:click="fnWrite">등록</button>
      </div>
      <el-table :data="tableData" style="width: 100%">
        <el-table-column prop="no" label="No" width="180" />
        <el-table-column prop="title" label="Title" width="180" />
        <el-table-column prop="author" label="Author" width="180" />
        <el-table-column prop="date" label="Date" />
      </el-table>
      <!-- <table class="w3-table-all">
        <thead>
        <tr>
          <th>No</th>
          <th>제목</th>
          <th>작성자</th>
          <th>등록일시</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="(row, idx) in list" :key="idx">
          <td>{{ row.idx }}</td>
          <td><a v-on:click="fnView(`${row.idx}`)">{{ row.title }}</a></td>
          <td>{{ row.author }}</td>
          <td>{{ row.created_at }}</td>
        </tr>
        </tbody>
      </table> -->
      <!-- <div class="pagination w3-bar w3-padding-16 w3-small" v-if="paging.total_list_cnt > 0">
        <span class="pg">
        <a href="javascript:;" @click="fnPage(1)" class="first w3-button w3-border">&lt;&lt;</a>
        <a href="javascript:;" v-if="paging.start_page > 10" @click="fnPage(`${paging.start_page-1}`)"
           class="prev w3-button w3-border">&lt;</a>
        <template v-for=" (n,index) in paginavigation()">
            <template v-if="paging.page==n">
                <strong class="w3-button w3-border w3-green" :key="index">{{ n }}</strong>
            </template>
            <template v-else>
                <a class="w3-button w3-border" href="javascript:;" @click="fnPage(`${n}`)" :key="index">{{ n }}</a>
            </template>
        </template>
        <a href="javascript:;" v-if="paging.total_page_cnt > paging.end_page"
           @click="fnPage(`${paging.end_page+1}`)" class="next w3-button w3-border">&gt;</a>
        <a href="javascript:;" @click="fnPage(`${paging.total_page_cnt}`)" class="last w3-button w3-border">&gt;&gt;</a>
        </span>
      </div> -->
    <!-- <div>
        <select v-model="search_key">
            <option value="">- 선택 -</option>
            <option value="title">제목</option>
            <option value="contents">내용</option>
        </select>
        <input type="text" v-model="search_value" @keyup.enter="fnPage()">
        <button @click="fnPage()">검색</button>
      </div> -->
    </div> 
  </template>
  
  <script lang="ts" setup>
  import { onMounted, ref } from 'vue';
  import router from '@/router';
  import axios from 'axios';
  import { ElTable, ElTableColumn } from 'element-plus';

  const tableData = ref([]);
  
  const getList = () => {
    axios.get('http://localhost:8081/board/list')
    .then((response) => {
      tableData.value = response.data;
    })
    .catch((error) => {
      console.error(error)
    });
  };

  const components = {
    ElTable,
    ElTableColumn,
  };

  onMounted(() => {
    getList();
  });

  const fnWrite = () => {
    router.push("./write");
  };
  </script>