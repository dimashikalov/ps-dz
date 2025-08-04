<script setup>
import Button from './components/Button.vue';
import Header from './components/Header.vue';
import Card from './components/Card.vue';
import { computed, onMounted, ref } from 'vue';

/*
Данные карточки
word - англ. перевод
translation - русский перевод
state - closed | opened - состояние карточки
status - success | fail | pending - состояние ответа
*/
const cardArray = ref([]);
let data = ref();

async function getCards() {
  const res = await fetch('http://localhost:8080/api/random-words');
  data.value = await res.json();
  console.log('res == ', data.value);
}

const computedArray = computed(() => {
  if (!data.value) return;
  cardArray.value = data.value.map((item, index) => ({
    id: index,
    cardNumber: String(index + 1).padStart(2, '0'),
    word: item.word,
    translation: item.translation,
    state: 'closed',
    status: 'pending',
  }));
});

onMounted(() => {
  getCards();
});

const flipCard = (state, id) => {
  const card = cardArray.value.find((item) => item.id === id);
  if (card) {
    card.state = state ? 'opened' : 'closed';
  }
};
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
        :card-number="item.cardNumber"
        :key="item.id"
        @flip-card="flipCard"
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
  flex-wrap: wrap;
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
