<script setup lang="ts">
import type { MenuProps } from 'ant-design-vue';
import {useRoute, useRouter} from "vue-router";
import {watch, ref} from "vue";
const route = useRoute()
const current = ref<string[]>(['']);
watch(()=>route.name,()=>{
  current.value[0] = <string>route.name
})
const router = useRouter()
const items = ref<MenuProps['items']>([
  {
    key: 'home',
    label: '首页',
    title: '首页',
  },
  {
    key: 'app',
    label: '技术栈',
    title: '技术栈',
  },
  {
    key: 'resolve',
    label: '难题or思路',
    title: '难题or思路',
  },
  {
    key: 'life',
    label: '生活',
    title: '生活',
  },
  {
    key: 'about',
    label: '关于',
    title: '关于',
  },
]);
function handleClickMenu(obj: object) {
  router.push({
    name: obj.key
  })
}
</script>

<template>
  <div class="menu-mask">
    <div class="tag">
      积极学习，积极生活
    </div>
    <a-menu v-model:selectedKeys="current"
            @click="handleClickMenu"
            mode="horizontal" :items="items" />
  </div>
</template>

<style lang="scss" scoped>
.menu-mask {
  display: flex;
  justify-content: space-between;
  background-color: #eee;
  opacity: 0.8;
  position: fixed;
  width: 100%;
  top: 0;
  left: 0;
  .tag {
    line-height: 47px;
    margin-left: 50px;
    font-size: 14px;
  }
  .ant-menu-overflow {
    :deep(.ant-menu-item) {
      margin: 0 20px;
    }
    :deep(.ant-menu-item-selected) {
      color: $active-color;
    }
    :deep(.ant-menu-item:hover) {
      color: $active-color;
    }
    :deep(.ant-menu-item:hover::after) {
      border-bottom-color: $active-color;
    }
    :deep(.ant-menu-item-selected::after) {
      border-bottom-color: $active-color;
    }
  }
  :deep(.ant-menu-horizontal) {
    border: 0;
  }
  :deep(.ant-menu-light) {
    background: unset;
  }
}
</style>