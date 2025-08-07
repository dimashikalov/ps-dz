<script setup>
import Score from './Score.vue';
</script>
<template>
  <header class="header">
    <h3>Запомни слово</h3>
    <Score />
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
