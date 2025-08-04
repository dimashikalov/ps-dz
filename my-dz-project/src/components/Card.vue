<script setup>
import Button from './Button.vue';
import IconClose from './../icons/IconClose.vue';
import IconSuccess from './../icons/IconSuccess.vue';
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

/*
Данные карточки
word - англ. перевод
translation - русский перевод
state - closed | opened - состояние карточки
status - success | fail | pending - состояние ответа 
*/
</script>

<template>
  <div class="card">
    <div class="card-header">
      {{ cardNumber }}
    </div>
    <template v-if="state == 'opened' && status == 'success'">
      <div class="card-icon"><IconSuccess :width="36" :height="36" /></div>
    </template>
    <template v-if="state == 'opened' && status == 'fail'">
      <div class="card-icon">
        <IconClose :width="36" :height="36" />
      </div>
    </template>
    <div class="card-content" v-if="state == 'closed'">
      {{ word }}
    </div>
    <div class="card-content" v-else>
      <!-- <div class="card-content" v-if="state == 'opened'"> -->
      {{ translation }}
    </div>
    <div class="card-footer" @click="flipCard()" v-if="state == 'closed'">
      ПЕРЕВЕРНУТЬ
    </div>
    <div
      class="card-footer"
      @click="flipCard()"
      v-else-if="state == 'opened' && status == 'pending'"
    >
      <Button class="card-button"><IconSuccess /></Button>
      <Button class="card-button"><IconClose /></Button>
    </div>
    <div class="card-footer" @click="flipCard()" v-else>Завершено</div>
  </div>
</template>
<style scoped>
.card-icon {
  margin-top: -28px;
  z-index: 1;
}
.card-button {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 25px;
  height: 25px;
  background-color: var(--color-primary);
  border: none;
}
.card {
  position: relative;
  width: 220px;
  height: 320px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
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
  display: flex;
}
.card-header {
  align-self: flex-start;
  margin-left: 15px;
}

.card-footer {
  align-self: center;
  gap: 15px;
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
