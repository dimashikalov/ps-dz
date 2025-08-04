<script setup>
import { ref } from 'vue';
import Score from './Score.vue';

const score = ref(10);
</script>
<template>
  <header class="header">
    <h3>Запомни слово</h3>
    <Score :score="score" />
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
