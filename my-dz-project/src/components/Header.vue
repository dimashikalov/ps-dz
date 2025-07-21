<script setup>
import Score from './Score.vue';

const likes = 25;
</script>
<template>
  <header class="header">
    <h3>Запомни слово</h3>
    <Score :likes="likes" />
  </header>
</template>

<style scoped>
.header {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  margin: 35px 65px;
}
</style>
