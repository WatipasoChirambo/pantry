<template>
  <div class="bg-surface-container-high rounded-lg p-4">

    <!-- Chart -->
    <div class="mt-6 w-full h-64 sm:h-72 md:h-80 block gap-5">
        <p class="font-bold text-black mb-4">Key Performance Indicators <span class="text-[gold]">(KPIs)</span></p>
      <Bar :data="chartData" :options="chartOptions" />
    </div>
  </div>
</template>

<script setup>
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
} from "chart.js";

import { Bar } from "vue-chartjs";

// Register ChartJS components
ChartJS.register(
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
);

// KPI data
const chartData = {
  labels: ["Revenue Growth", "Member Compliance", "Admin Overhead"],
  datasets: [
    {
      label: "KPI Values (%)",
      data: [12.4, 94, -2.1], // your values
      backgroundColor: [
        "#4CAF50", // green (positive)
        "#1E90FF", // blue (high positive)
        "#FF4C4C"  // red (negative)
      ],
      borderRadius: 6
    }
  ]
};

const chartOptions = {
  responsive: true,
  maintainAspectRatio: false,
  plugins: {
    legend: {
      display: false
    },
    tooltip: {
      callbacks: {
        label: (ctx) => `${ctx.raw}%`
      }
    }
  },
  scales: {
    y: {
      beginAtZero: false, // ✅ allows negative values to show
      min: -10,           // ✅ gives space below -2.1
      max: 300,           // ✅ fits 94% nicely
      ticks: {
        stepSize: 20,     // ✅ increments: 0, 10, 20, 30...
        callback: (val) => `${val}%`
      }
    }
  }
};
</script>