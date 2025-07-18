<script setup></script>
<template>
  <button class="button">
    <slot />
  </button>
</template>
<style scoped>
.button {
  width: 315px;
  padding: 16px 10px;
  border-radius: 100px;
  text-align: center;
  border: none;
  background-color: var(--color-secondary);
  /* background-color: #008bfe; */
  color: #ffffff;
  cursor: pointer;
  font-size: 24px;
  font-weight: 400;
}

.button:hover {
  background-color: #006fcb;
}
</style>
