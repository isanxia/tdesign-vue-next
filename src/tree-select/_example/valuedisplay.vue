<template>
  <div class="tdesign-demo-block-row">
    <t-tree-select v-model="value" :data="options" clearable placeholder="请选择">
      <template #valueDisplay="{ value: valueDisplay }"> {{ valueDisplay.label }}({{ valueDisplay.value }}) </template>
    </t-tree-select>
    <t-tree-select
      v-model="mulValue"
      class="tree-select-multiple"
      :data="options"
      multiple
      clearable
      filterable
      placeholder="请选择"
    >
      <template #valueDisplay="{ value: valueDisplay, onClose }">
        <t-tag v-for="(item, index) in valueDisplay" :key="index" closable :on-close="() => onClose(index)">
          {{ item.label }}({{ item.value }})
        </t-tag>
      </template>
    </t-tree-select>
  </div>
</template>
<script setup>
import { ref } from 'vue';

const value = ref('shenzhen');
const mulValue = ref(['shenzhen', 'guangzhou']);
const options = [
  {
    label: '广东省',
    value: 'guangdong',
    children: [
      {
        label: '广州市',
        value: 'guangzhou',
      },
      {
        label: '深圳市',
        value: 'shenzhen',
      },
    ],
  },
  {
    label: '江苏省',
    value: 'jiangsu',
    children: [
      {
        label: '南京市',
        value: 'nanjing',
      },
      {
        label: '苏州市',
        value: 'suzhou',
      },
    ],
  },
];
</script>
<style scoped>
.tdesign-tree-select-valuedisplay {
  width: 300px;
  margin: 0 20px;
}
.tree-select-multiple {
  margin-top: 20px;
}
</style>
