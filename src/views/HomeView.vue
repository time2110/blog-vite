<script setup lang="ts">
import {useRouter} from "vue-router";
const router = useRouter()
function handleClick() {
  router.push({
    name: 'about'
  })
}
</script>

<template>
  <div class="home-container flex-center">
    <a-card :bordered="false">
      <p>记录个人成长之路</p>
      <p>生活就是不断前进的旅程——奥利维亚·怀尔德</p>
      <a-button type="primary" @click="handleClick">个人信息 -></a-button>
    </a-card>
  </div>
</template>

<style scoped lang="scss">
  .home-container {
    height: 100%;
    .ant-card {
      background-color: unset;
      padding: 20px;
      p:nth-child(1) {
        font-size: 24px;
      }
      p:nth-child(2) {
        font-size: 16px;
        color: gray;
      }
      .ant-btn {
        margin-top: 20px;
      }
    }
  }
</style>