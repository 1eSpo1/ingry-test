<template>
  <div :class="$style.wrapper">
  <BarChart :class="$style.chart" :chartData="chartData" :chart-colors="chartData.backgroundColor"/>
    <div :class="$style.labels">
        <template  v-for="(label, index) in chartData.labels">
          <div :class="$style.label">
            <div>
              <div :class="$style.prefix" :style="`background-color: ${chartData.backgroundColor[index]}`" />
              <span>{{ label }} </span>
            </div>
            <span>{{chartData.datasets[0].data[index]}}</span>
          </div>
        </template>
    </div>
  </div>
</template>

<script setup lang="ts">
import BarChart from "./BarChart/BarChart.vue";
import type {PropType} from "vue";

type TDataset = {
  data: number[],
  borderRadius: number
}
interface ChartData {
  labels: string[],
  datasets: TDataset[],
  backgroundColor: string[]
}

const { chartData } = defineProps({
  chartData: {
    type: Object as PropType<ChartData>,
    required: true
  },
})
</script>

<style module>

.wrapper {
  display: flex;
  flex-direction: column;
  width: 100%;
  border: 1px solid rgba(204, 204, 204, 1);
  border-radius: 12px;
  padding: 16px;
  height: 208px;
}

.chart {
  padding-bottom: 12px;
}
.labels {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 24px;
}

.label {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.prefix {
  content: '';
  display: inline-block;
  color: #000;
  width: 24px;
  height: 8px;
  text-align: center;
  border-radius: 4px 4px 0 0;
  box-sizing: border-box;
  margin-right: 8px;
}

</style>