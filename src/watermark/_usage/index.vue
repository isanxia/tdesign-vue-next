<!-- 该脚本为自动生成，如有需要请在 /script/generate-usage/index.js 中调整 -->
<template>
  <base-usage :code="usageCode" :config-list="configList" :panel-list="panelList" @panel-change="onPanelChange">
    <template #watermark="{ configProps }"
      ><t-watermark v-bind="configProps" content="文字水印" :y="120" :x="80">
        <div style="width: 100%; height: 100%" /> </t-watermark
    ></template>
  </base-usage>
</template>

<script setup lang="jsx">
/* eslint-disable */
import { ref, onMounted } from 'vue';
import configJson from './props.json';

const configList = ref(configJson);
const panelList = [{ label: 'watermark', value: 'watermark' }];

const usageCodeMap = {
  watermark:
    '\n        <t-watermark v-bind="configProps" content="文字水印" :y="120" :x="80">\n          <div style="width: 100%; height: 100%" />\n        </t-watermark>\n      ',
};
const usageCode = ref(`<template>${usageCodeMap[panelList[0].value].trim()}</template>`);

function onPanelChange(panel) {
  usageCode.value = `<template>${usageCodeMap[panel].trim()}</template>`;
}
</script>
