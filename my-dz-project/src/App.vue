<script setup>
import Button from './components/Button.vue';
import Header from './components/Header.vue';
import Card from './components/Card.vue';

const cardNumber = '01';
const word = 'unadmitted';
</script>

<template>
  <main>
    <Header />

    <div class="content">
      <Button>Начать игру</Button>
      <Card :card-number="cardNumber" :word="word" />
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
