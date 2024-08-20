<template>
  <aside :class="`${is_expanded ? $style.is_expanded : ''}`">
    <div class="logo">
    </div>

    <div :class="$style.menu_toggle_wrap">
      <button class="menu-toggle" @click="ToggleMenu">
        <IconLeft :class="`${is_expanded ? '' : $style.arrow_is_expanded}`" />
      </button>
    </div>

    <div :class="$style.menu">
      <span>Дашборд</span>
      <span>Сеть</span>
      <span>Безопасность</span>
    </div>

    <div class="flex"></div>


  </aside>
</template>

<script setup lang="ts">
import {ref} from "vue";
import IconLeft from "@/components/icons/IconLeft.vue";

const is_expanded = ref(true)

const ToggleMenu = () => {
  is_expanded.value = !is_expanded.value
}
</script>

<style module>
aside {
  position: relative;
  display: flex;
  flex-direction: column;
  border-right: 1px solid rgba(204, 204, 204, 1);
  width: calc(2rem + 32px);
  overflow: hidden;
  min-height: 100vh;
  padding: 32px;

  transition: 0.2s ease-in-out;

}
.is_expanded {
  width: 300px;

  .menu-toggle-wrap {
    top: -3rem;

    .menu-toggle {
      transform: rotate(-180deg);
    }
  }
}
.menu {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.menu_toggle_wrap {
  position: absolute;
  bottom: 12px;
  left: 12px;
}

.arrow_is_expanded {
  transform: rotate(180deg);
}
</style>