<script setup>
import Button from './components/Button.vue';
import Header from './components/Header.vue';
import Card from './components/Card.vue';
import { ref } from 'vue';

const cardNumber = '01';

const cardState = ref({
  word: 'unadmitted!!!',
  translation: 'Перевод',
  state: 'closed',
  status: 'pending',
});
</script>

<template>
  <main>
    <Header />

    <div class="content">
      <Button>Начать игру</Button>
      <Card v-bind="cardState" :card-number="cardNumber" />
    </div>
  </main>
</template>

<style scoped>
.content {
  display: flex;
  justify-content: center;
  height: 80vh;
  align-items: center;
}
</style>
