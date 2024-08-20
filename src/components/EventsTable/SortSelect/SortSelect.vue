<template>
  <select  @change="$emit('sort', $event)">
    <option class="option" value="date">Сортировать по дате создания</option>
    <option class="option" value="status">Сортировать по Статусу</option>
    <option class="option" value="importance">Сортировать по Уровню важности</option>
    <option class="option" value="node">Сортировать по Узлу</option>
    <option class="option" value="category">Сортировать по Категории</option>
  </select>
</template>

<script setup lang="ts">
const emit = defineEmits(['sort'])
</script>

<style module>

</style>