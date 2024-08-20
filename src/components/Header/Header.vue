<script setup lang="ts">

import IconBell from "../icons/IconBell.vue";
import IconMagnifyingGlass from "@/components/icons/IconMagnifyingGlass.vue";
</script>

<template>
    <header :class="$style.wrapper">
      <button :class="$style.button">
        <IconMagnifyingGlass />
      </button>
      <button :class="$style.button">
        <IconBell />
      </button>
      <select :class="$style.select">
        <option class="option" value="1">admin</option>
      </select>
    </header>
</template>

<style module>
.wrapper {
  width: 100%;
  display: flex;
  align-items: center;
  gap: 12px;
  justify-content: flex-end;
  padding: 18px 20px;
  border-bottom: 1px solid rgba(204, 204, 204, 1);
}

.button {
  flex-wrap: wrap;
  border-radius: 50%;
  display: flex;
  place-content: center;
  height: 36px;
  width: 36px;
  border: 1px solid rgba(204, 204, 204, 1)
}


.select {
  border: 1px solid rgba(204, 204, 204, 1);
  border-radius: 44px;
  padding: 8px 0 8px 32px;
  background-image: url('src/assets/user-bold.svg');
  background-repeat: no-repeat;
  background-position: 6px;
  width: 142px;
  position: relative;
}
</style>