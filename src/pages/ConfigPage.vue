<template>
  <div id="customConfigPage">
   
  </div>
</template>
<script setup lang="ts">
import { reactive, ref } from "vue";
import { FormInstance } from "ant-design-vue";
import { useRouter } from "vue-router";
import { useGlobalStore } from "../core/globalStore";
import { defaultGameConfig } from "../core/gameConfig";

const formRef = ref<FormInstance>();
const router = useRouter();
const { customConfig, setGameConfig, setCustomConfig, reset } =
  useGlobalStore();
const initConfig = {
  randomAreaNum: 2,
  randomBlockNum: 8,
  animalStr: defaultGameConfig.animals.join(""),
  ...customConfig,
};
const config = reactive<any>(initConfig);



const resetForm = () => {
  formRef?.value?.resetFields();
};

/**
 * 还原至初始配置
 */
const resetConfig = () => {
  reset();
  router.go(0);
};

/**
 * 回上一页
 */
const doBack = () => {
  router.back();
};
</script>
<style></style>
