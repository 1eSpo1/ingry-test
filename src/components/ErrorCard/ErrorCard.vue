<template>
  <div :class="$style.wrapper">
    <span :class="$style.title" :style="`background-color: ${color}`">{{ amount}}</span>
    <span :class="$style.text"> {{ text }}</span>
  </div>
</template>

<script setup lang="ts">
const { amount, text } = defineProps({
  amount: Number,
  text: String,
  color: String,
})
</script>

<style module>
.wrapper {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 8px;
  border: 1px solid rgba(204, 204, 204, 1);
  border-radius: 12px;
  padding: 16px;
}

.title {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 40px;
  width: 40px;
  color: white;
  border-radius: 50%;
}

.text {
  font-weight: 400;
  font-size: 14px;
  line-height: 20px;
}

</style>
