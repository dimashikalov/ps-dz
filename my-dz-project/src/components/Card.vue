<script setup>
// const { cardNumber } = defineProps({
//   cardNumber: String,
// });
const { translation, word, state, status, cardNumber } = defineProps({
  word: String,
  translation: String,
  state: String,
  status: String,
  cardNumber: String,
});
const emit = defineEmits(['flip-card', 'change-status']);

function flipCard() {
  emit('flip-card', true);
}
// function changeStatus() {
//   emit('change-status', true);
// }
</script>
<template>
  <div class="card">
    <div class="card-header">
      {{ cardNumber }}
    </div>
    <div class="card-content">
      {{ word }}
    </div>
    <div class="card-footer" @click="flipCard()">ПЕРЕВЕРНУТЬ</div>
  </div>
</template>
<style scoped>
.card {
  position: relative;
  width: 220px;
  height: 320px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 16px;
  background: var(--color-primary);
  text-align: center;
  overflow: hidden;
}
.card::before {
  content: '';
  position: absolute;
  top: 25px;
  left: 19px;
  right: 19px;
  bottom: 25px;
  border: 1px solid var(--color-light-blue);
  border-radius: 12px;
  pointer-events: none;
  z-index: 0;
}
.card-header,
.card-footer {
  position: relative;
  z-index: 1;
  padding: 0 3px;
  background: var(--color-primary);
  width: min-content;
}
.card-header {
  align-self: flex-start;
  margin-left: 15px;
}

.card-footer {
  align-self: center;
}
.card-content {
  font-size: 20px;
  font-weight: 500;
  color: var(--color-text);
  flex-grow: 1;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
