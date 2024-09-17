<template>
  <radar :data="data" style="width:500px" />
</template>

<script setup>
import radar from './components/radar.vue';
const data = [
  { item: 'Design', user: '企业数', score: 90 },
  { item: 'Design', user: '设备数', score: 10 },
  { item: 'Development', user: '企业数', score: 80 },
  { item: 'Development', user: '设备数', score: 20 },
  { item: 'Marketing', user: '企业数', score: 70 },
  { item: 'Marketing', user: '设备数', score: 30 },
  { item: 'Users', user: '企业数', score: 60 },
  { item: 'Users', user: '设备数', score: 40 },
  { item: 'Test', user: '企业数', score: 50 },
  { item: 'Test', user: '设备数', score: 50 },
  { item: 'Language', user: '企业数', score: 40 },
  { item: 'Language', user: '设备数', score: 60 },
  { item: 'Technology', user: '企业数', score: 30 },
  { item: 'Technology', user: '设备数', score: 70 },
];
</script>

<style scoped></style>
