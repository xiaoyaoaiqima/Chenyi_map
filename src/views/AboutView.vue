<template>
  <div>
    <input type="text" v-model="inputTime" placeholder="输入时间">
    <button @click="showEvent">显示事件</button>
    <div id="map"></div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
<script setup>
const good = false;
</script>