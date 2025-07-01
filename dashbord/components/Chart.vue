<template>
  <div>
    <canvas ref="chartCanvas"></canvas>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { Chart, registerables } from 'chart.js'

// Register all Chart.js components
Chart.register(...registerables)

const chartCanvas = ref(null)

onMounted(() => {
  const data = {
    labels: ['Smart Watch', 'Wireless Earbuds', 'Gaming Laptop', 'Bluetooth Speaker'],
    datasets: [{
      label: 'Products',
      data: [12, 19, 3, 5, 2, 3],
      backgroundColor: [
        'rgba(255, 99, 132, 0.6)',
        'rgba(54, 162, 235, 0.6)',
        'rgba(255, 206, 86, 0.6)',
        'rgba(75, 192, 192, 0.6)',
        'rgba(153, 102, 255, 0.6)',
        'rgba(255, 159, 64, 0.6)'
      ],
      borderColor: 'rgba(0, 0, 0, 0.2)',
      borderWidth: 1
    }]
  }

  const config = {
    type: 'bar',
    data: data,
    options: {
      responsive: true,
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
