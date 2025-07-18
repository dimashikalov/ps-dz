<script setup>
import IconLikes from '../icons/IconLikes.vue';
const props = defineProps({
  likes: Number,
});
</script>
<template>
  <div class="score">
    <div class="likes-container">
      <span>{{ props.likes }}</span>
      <IconLikes />
    </div>
  </div>
</template>
<style scoped>
.score {
  width: 110px;
  height: 48px;
  align-content: center;
  padding: 12px 24px;
  background: var(--color-light-blue);
  color: var(--color-secondary);
  border-radius: 36px;
  text-align: center;
}
.likes-container {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}
</style>
