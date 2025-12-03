<template>
  <div class="bg-brand-graphite p-6 rounded-xl border border-gray-800 shadow-lg">
     <h3 class="text-lg font-bold text-white mb-4">نمودار بازدید هفتگی</h3>
    <Line :data="chartData" :options="chartOptions" />
  </div>
</template>

<script setup>
import { Line } from 'vue-chartjs';
import { Chart as ChartJS, Title, Tooltip, Legend, LineElement, CategoryScale, LinearScale, PointElement, Filler } from 'chart.js';
import { ref } from 'vue';

ChartJS.register(Title, Tooltip, Legend, LineElement, CategoryScale, LinearScale, PointElement, Filler);

// Mock data for chart
const chartData = ref({
  labels: ['شنبه', '۱شنبه', '۲شنبه', '۳شنبه', '۴شنبه', '۵شنبه', 'جمعه'],
  datasets: [
    {
      label: 'بازدیدها',
      borderColor: '#0A84FF',
      backgroundColor: (context) => {
          const ctx = context.chart.ctx;
          const gradient = ctx.createLinearGradient(0, 0, 0, 200);
          gradient.addColorStop(0, 'rgba(10, 132, 255, 0.5)');
          gradient.addColorStop(1, 'rgba(10, 132, 255, 0)');
          return gradient;
        },
      borderWidth: 3,
      pointBackgroundColor: 'white',
      pointBorderColor: '#0A84FF',
      pointHoverRadius: 7,
      pointRadius: 5,
      tension: 0.4, // Makes the line smooth
      fill: true,
      data: [45, 60, 55, 80, 75, 90, 85],
    },
  ],
});

const chartOptions = ref({
  responsive: true,
  maintainAspectRatio: false,
  plugins: {
    legend: {
      display: false,
    },
    tooltip: {
        backgroundColor: '#1C1C1E',
        titleFont: { size: 14, family: 'peyda' },
        bodyFont: { size: 12, family: 'peyda' },
        padding: 10,
        cornerRadius: 8,
        boxPadding: 4,
    }
  },
  scales: {
    x: {
      grid: {
        color: 'rgba(255, 255, 255, 0.1)',
        borderColor: 'rgba(255, 255, 255, 0.1)'
      },
      ticks: {
        color: '#9CA3AF', // Text color for x-axis labels
        font: { family: 'peyda' }
      }
    },
    y: {
      grid: {
        color: 'rgba(255, 255, 255, 0.05)',
        borderColor: 'rgba(255, 255, 255, 0.1)'
      },
      ticks: {
        color: '#9CA3AF', // Text color for y-axis labels
        font: { family: 'peyda' }
      }
    }
  }
});
</script>
