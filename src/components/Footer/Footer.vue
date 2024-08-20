<template>
  <footer :class="$style.footer">
    <span :class="$style.copyright">Текущие задачи: 0 из 0</span>
     <IconArrowUp />
  </footer>
</template>

<script setup lang="ts">

import IconArrowUp from "@/components/icons/IconArrowUp.vue";
</script>

<style module>
.footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 60px;
  border-top: 1px solid rgba(204, 204, 204, 1);
  padding: 0 32px;
}

.copyright {
  font-size: 14px;
  font-weight: 400;
  color: #999999;
  display: flex;
  align-items: center;

}
.copyright::before {
  content: url("src/assets/stack-bold.svg");
  margin-right: 8px;

}
</style>