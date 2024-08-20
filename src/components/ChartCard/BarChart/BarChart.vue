<template>
  <Bar
      id="my-chart-id"
      :options="chartOptions"
      :data="chartData"
      :class="$style.chart"
  />
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'



ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  props: {
    chartData: {
      type: Object,
      required: true
    },
    chartColors: {
      type: Array,
      required: true
    }
  },
  components: { Bar },
  data() {
    return {
      chartData: this.chartData,
      chartOptions: {
        responsive: true,
        aspectRatio: 6,
        devicePixelRatio: 4,
        plugins: {
          legend: {
            display: false
          }
        },
        backgroundColor: this.chartColors,
        scales: {
          x: {
            grid: {
              display: false
            },
            ticks: {
              display: false,
            }
          },
          y: {
            ticks: {
              stepSize: 8,
              beginAtZero: true,
              backdropColor: '#F5F5F5',
              showLabelBackdrop: true,

            },
            grid: {
              display: false,
            },
            border: {
              display: false
            }
          }
        }
      }
    }
  }
}
</script>

<style module>
.chart {
  width: 100% !important;
}

</style>