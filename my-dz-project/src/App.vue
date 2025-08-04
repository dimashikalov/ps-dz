<script setup>
import Button from './components/Button.vue';
import Header from './components/Header.vue';
import Card from './components/Card.vue';
import { ref } from 'vue';

/*
Данные карточки
word - англ. перевод
translation - русский перевод
state - closed | opened - состояние карточки
status - success | fail | pending - состояние ответа 
*/
const cardNumber = '01';
const cardArray = ref([
  {
    id: '01',
    word: 'unadmitted!!!',
    translation: 'Перевод',
    state: 'closed',
    status: 'pending',
  },
  {
    id: '02',
    word: 'unadmitted!!!',
    translation: 'Перевод',
    state: 'opened',
    status: 'pending',
  },
  {
    id: '03',
    word: 'unadmitted!!!',
    translation: 'Перевод',
    state: 'opened',
    status: 'success',
  },
  {
    id: '04',
    word: 'unadmitted!!!',
    translation: 'Перевод',
    state: 'opened',
    status: 'fail',
  },
]);

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
      <Button class="button">Начать игру</Button>
    </div>
    <div class="cards-content">
      <Card
        v-for="item in cardArray"
        v-bind="item"
        :card-number="item.id"
        :key="item.id"
      />
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
.cards-content {
  display: flex;
  gap: 10px;
  justify-content: center;
  align-items: center;
}
.button {
  width: 315px;
  padding: 16px 10px;
  border-radius: 100px;
  text-align: center;
  border: none;
  background-color: var(--color-secondary);
  color: #ffffff;
  cursor: pointer;
  font-size: 24px;
  font-weight: 400;
}

.button:hover {
  background-color: #006fcb;
}
</style>
