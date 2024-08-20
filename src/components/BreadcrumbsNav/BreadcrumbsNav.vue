<script setup lang="ts">

</script>

<template>
  <nav aria-label="Breadcrumb" class="breadcrumb">
    <ul>
      <li><a href="#">Главная</a></li>
      <li><a href="#" style="color: #808080">Мониторинг ошибок</a></li>
    </ul>
  </nav>
</template>

<style scoped>
.breadcrumb {
  padding: 32px 32px 0 32px;

}

.breadcrumb ul {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  list-style: none;
  margin: 0;
  padding: 0;
}

.breadcrumb li {
  font-size: 14px;
  font-weight: 400;

  display: flex;
  align-items: center;
}

.breadcrumb li:not(:last-child)::after {
  content: url("src/assets/dot-bold.svg");
}
</style>