<template>
  <Header />
  <main :class="$style.page">
    <Sidebar />
    <div :class="$style.wrapper">
      <BreadcrumbsNav />
      <div :class="$style.refresh">
        <span :class="$style.title">Мониторинг ошибок</span>
        <button :class="$style.button" @click="handleRefresh">Обновить</button>
      </div>
      <div :class="$style.cards_wrapper">
        <div :class="$style.cards">
          <ErrorCard
              :amount="12"
              :text="'Сети'"
              :color="'#0197F0'"
          >
          </ErrorCard>
          <ErrorCard
              :amount="1"
              :text="'Безопасность'"
              :color="'#EC34F0'"
          />
          <ErrorCard
              :amount="3"
              :text="'Окружение'"
              :color="'#5D6095'"
          />
          <ErrorCard
              :amount="0"
              :text="'Система'"
              :color="'#2DB57D'"
          />
        </div>
        <div :class="$style.cards">
          <ChartCard :chart-data="firstChartData" />
          <ChartCard :chart-data="secondChartData" />
        </div>
      </div>
      <EventsTable />
      <Footer />
    </div>

  </main>
</template>

<script setup lang="ts">
import Header from './components/Header/Header.vue'
import BreadcrumbsNav from "./components/BreadcrumbsNav/BreadcrumbsNav.vue";
import EventsTable from "@/components/EventsTable/EventsTable.vue";
import ErrorCard from "@/components/ErrorCard/ErrorCard.vue";
import ChartCard from "@/components/ChartCard/ChartCard.vue";
import Sidebar from "@/components/Sidebar/Sidebar.vue";
import {ref} from "vue";
import Footer from "@/components/Footer/Footer.vue";

const firstChartData = ref({
  labels: [ 'Ошибки сети', 'Безопасность', 'Окружение', 'Система' ],
  datasets: [ { data: [12, 1, 3, 0], borderRadius: 10 } ],
  backgroundColor: [ '#0197F0', '#EC34F0', '#5D6095', '#2DB57D' ]
})

const secondChartData = {
  labels: [ 'Критические', 'Средние',  ],
  datasets: [ { data: [4, 12], borderRadius: 10 } ],
  backgroundColor: [ '#FF4F13', '#FFC000' ]
}


const handleRefresh = () => {
  window.location.reload()
}
</script>


<style module>

.page {
  display: flex;
}
.wrapper {
  display: flex;
  width: 100%;
  flex-direction: column;
  gap: 32px;

}

.refresh {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 32px ;
}
.cards_wrapper {
  padding: 0 32px;
}
.cards {
  display: flex;
  padding-bottom: 8px;
  gap: 8px;

}

.title {
  font-size: 22px;
  font-weight: 500;
  line-height: 28px;
}

.button {
  display: flex;
  align-items: center;
}
.button::before {
  content: url("src/assets/arrow-clockwise-bold.svg");
  margin-right: 8px;

}
</style>
