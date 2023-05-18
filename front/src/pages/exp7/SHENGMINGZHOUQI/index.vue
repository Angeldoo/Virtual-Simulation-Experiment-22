<template>

<div type="flex" justify-content="center" style="height:50px">
    <div style="float:left">
      <h1 class="title">{{ $route.meta.title }} </h1>
    </div>
    <div style="float:right">
      <a-button style="margin-right:20px" type="primary" shape="round" @click="downLoadFile">
        <template #icon >
          <DownloadOutlined  />
        </template>实验指导书下载
      </a-button>
      <a-button class="button2" type="primary" shape="round">
        <template #icon>
          <DownloadOutlined />
        </template>实验报告模板下载
      </a-button>
    </div>
  </div>
  <hr />
    

</template>



<script lang="ts">
import { Document } from '@element-plus/icons-vue'
import { defineComponent } from 'vue'
export default {
    name: 'SHENGMINGZHOUQI',
}
</script>

<style scoped>

</style> 
