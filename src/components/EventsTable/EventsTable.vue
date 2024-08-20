<template>
  <div :class="$style.buttons">
    <input type="text" @input="handleSearch" :class="$style.button" placeholder="Поис по имени">
    <SortSelect :class="$style.button" @sort="handleSort" />
    <button :class="$style.button" @click="handleFilter">
      Расширенный фильтр
    </button>
  </div>
  <table :class="$style.table">
    <thead>
    <tr :class="$style.header_row">
      <th :class="$style.header_cell" style="width: 32px"><input type="checkbox" :class="$style.checkbox" @change="handleSelectAll" v-model="allSelect"></th>
      <th :class="$style.header_cell" v-for="item in themes" :key="item">{{ item }}</th>
    </tr>
    </thead>
    <tbody >
    <tr v-for="item in filteredData" :key="item.id">
        <td :class="$style.body_cell" style="width: 32px"><input type="checkbox" :class="$style.checkbox" @change="handleSelect" :value="item.id" v-model="selected"></td>
        <td :class="$style.body_cell" v-if="item.event" >{{ item.event }}</td>
        <td :class="$style.body_cell" v-if="item.category" >{{ item.category }}</td>
        <td :class="$style.body_cell" v-if="item.node" >{{ item.node }}</td>
        <td :class="$style.body_importance_cell" v-if="item.importance" >
          <div :class="$style.body_importance_cell_prefix" :style="{ backgroundColor: item.importance === 'Средний' ? '#7030A0' : '#FF4F13'}"/>
          {{ item.importance }}
        </td>
        <td :class="$style.body_cell" v-if="item.date" >{{ item.date }}</td>
        <td :class="$style.body_cell" v-if="item.status" >
          <div :class="$style.body_status_cell" :style="{ backgroundColor: item.status === 'Решено' ? '#2DB57D' : '#DE1E59'}">
            {{ item.status }}
          </div>
        </td>
    </tr>
    </tbody>
  </table>
</template>

<script setup lang="ts">
import {MOCK_DATA, MOCK_THEMES} from "@/constants";
import {computed, reactive, ref, watch} from "vue";
import SortSelect from "@/components/EventsTable/SortSelect/SortSelect.vue";

const data = reactive(MOCK_DATA);
const themes = reactive(MOCK_THEMES);
const selected = ref<string[] >([])
const allSelect = ref(false)
const searchFilter = ref('')


const handleFilter = () => {
  // TODO : Добавить фильтр
  alert('Здесь мог быть ваш фильтр')
}

const handleSelectAll = () => {
  if (allSelect.value) {
    selected.value = data.map(item => item.id.toString())
    allSelect.value = false
  } else {
    selected.value = []
    allSelect.value = true
  }
}

const handleSelect = () => {
  allSelect.value = selected.value.length === data.length;
}

const isAllSelectedData = watch( selected, () => {
  allSelect.value = selected.value.length === data.length;
})


const filteredData = computed(() => {
  if (searchFilter.value !== '') {
    console.log(searchFilter.value)
    return data.filter(item => item.event?.toLowerCase().includes(searchFilter.value.toLowerCase()))
  }
  return data;
})

const handleSearch = (e: Event) => {
  const target = e.target as HTMLInputElement;
  searchFilter.value = target.value;
}

const handleSort = (e: Event) => {
  const target = e.target as HTMLSelectElement;
  console.log(target.value)
  filteredData.value.sort((a: any, b: any) => {
    if (a[target.value] < b[target.value]) {
      return -1
    }
    if (a[target.value] > b[target.value]) {
      return 1
    }
    return 0
  })
}
</script>

<style module>

.buttons {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 8px;
  padding-right: 32px;
}

.button {
  border: 1px solid rgba(204, 204, 204, 1);
  border-radius: 8px;
  padding: 12px;
  font-size: 14px;
  font-weight: 400;
}
.table {
  table-layout: fixed;
  border-spacing: 0;
  padding: 0 32px;
}

.header_row {
  height: 56px;
}

.header_cell {
  text-align: center;
  border-bottom: 1px solid rgba(204, 204, 204, 1);

  border-collapse: collapse;
}

.header_cell:nth-child(2) {
  text-align: left;
}

.header_cell:last-child {
  text-align: right;
}

.body_cell {
  text-align: center;
  height: 56px;
}

.body_cell:nth-child(2) {
  text-align: left;
  padding-left: 8px;
}
.body_cell:last-child {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}

.body_status_cell {
  border-radius: 16px;
  padding: 4px 8px 4px 8px;
  background-color: green;
  color: white;
  width: fit-content;
  text-align: right;
}

.body_importance_cell {
  display: flex;
  align-items: center;
  justify-content: center;
}

.body_importance_cell_prefix {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  margin-right: 8px;
}

.checkbox {
  width: 16px;
  height: 16px;
}
</style>