
<template>
  <div>
    <canvas ref="chartCanvas"></canvas>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { Chart, registerables } from 'chart.js'

Chart.register(...registerables)

const chartCanvas = ref(null)

onMounted(() => {
  const data = {
    labels: ['January', 'February', 'March', 'April', 'May'],
    datasets: [{
      label: 'Sales',
      data: [10, 25, 15, 30, 20],
      fill: false,
      borderColor: 'rgb(75, 192, 192)',
      tension: 0.3
    }]
  }

  const config = {
    type: 'line',
    data: data,
    options: {
      responsive: true,
      plugins: {
        legend: {
          display: true
        }
      },
      scales: {
        y: {
          beginAtZero: true
        }
      }
    }
  }

  new Chart(chartCanvas.value, config)
})
</script>

<style scoped>

</style>
