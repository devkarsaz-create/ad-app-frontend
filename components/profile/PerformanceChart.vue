<template>
  <Line :data="chartData" :options="chartOptions" />
</template>

<script setup>
import { Line } from 'vue-chartjs';
import { Chart as ChartJS, CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend, Filler } from 'chart.js';
import { ref, computed } from 'vue';

ChartJS.register(CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend, Filler);

const chartData = computed(() => ({
  labels: ['شنبه', 'یکشنبه', 'دوشنبه', 'سه‌شنبه', 'چهارشنبه', 'پنج‌شنبه', 'جمعه'],
  datasets: [
    {
      label: 'بازدیدها',
      data: [65, 59, 80, 81, 56, 55, 90],
      fill: true,
      borderColor: '#3b82f6', // brand-blue
      backgroundColor: (context) => {
          const ctx = context.chart.ctx;
          const gradient = ctx.createLinearGradient(0, 0, 0, 300);
          gradient.addColorStop(0, 'rgba(59, 130, 246, 0.4)');
          gradient.addColorStop(1, 'rgba(59, 130, 246, 0)');
          return gradient;
      },
      tension: 0.4, // Makes the line curvy
      pointBackgroundColor: '#ffffff',
      pointBorderColor: '#3b82f6',
      pointHoverRadius: 8,
      pointHoverBackgroundColor: '#3b82f6',
    },
  ],
}));

const chartOptions = ref({
  responsive: true,
  maintainAspectRatio: false,
  plugins: {
    legend: {
      display: false, // Hide the legend
    },
    tooltip: {
      rtl: true,
      direction: 'rtl',
      backgroundColor: 'rgba(17, 24, 39, 0.8)', // bg-gray-900
      titleFont: { family: 'IRANSans', weight: 'bold', size: 14 },
      bodyFont: { family: 'IRANSans', size: 12 },
      padding: 12,
      cornerRadius: 8,
      displayColors: false, // Hide the little color box
    },
  },
  scales: {
    y: {
      beginAtZero: true,
      grid: {
        color: 'rgba(255, 255, 255, 0.1)', // Subtle grid lines
        borderDash: [5, 5], // Dashed lines
      },
      ticks: {
        color: '#9ca3af', // text-gray-400
        font: { family: 'IRANSans' },
      },
    },
    x: {
      grid: {
        display: false, // Hide vertical grid lines
      },
      ticks: {
        color: '#9ca3af', // text-gray-400
        font: { family: 'IRANSans' },
      },
    },
  },
});
</script>
