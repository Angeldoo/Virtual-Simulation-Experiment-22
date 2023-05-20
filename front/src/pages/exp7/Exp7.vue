<!-- 7.软件项目/产品的不确定性实验(大类)
包括: 最大最小法、最小后悔值法、最大最大法等 -->

<template>
  <div style="padding:2%">

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
  <RouterView />
</div>
</template>

<script lang="ts" setup>
import { useExperimentStore } from '@/store/experiment';
import { useRoute } from 'vue-router';
const { getExperiment } = useExperimentStore();
const rt = useRoute()

function downLoadFile(){
  getExperiment(rt.meta.id)
    .then((res) => {
      console.log(res.file)
      const fileName = res.file
      if (!fileName) {
        return;
      }
      let url = window.URL.createObjectURL(new Blob([fileName]));
      let link = document.createElement('a');
      link.style.display = 'none';
      link.href = url;
      link.setAttribute('download', fileName);
      document.body.appendChild(link);
      link.click();
    })
}

</script>

<style scoped lang="less">
.title {
  font-family: sans-serif;
  font-size: 30px;
}
</style>
