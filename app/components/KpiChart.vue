<template>
  <div class="bg-surface-container-high rounded-lg p-4">

    <!-- Chart -->
    <div class="mt-6 w-full h-64 sm:h-72 md:h-80 block gap-5">
      <p class="font-bold text-black mb-4">
        Key Performance Indicators <span class="text-[gold]">(KPIs)</span>
      </p>
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

// ✅ KPI data based on your financial information
const chartData = {
  labels: [
    "Revenue Growth",
    "Investment Income Growth",
    "Surplus Growth"
  ],
  datasets: [
    {
      label: "KPI Values (%)",
      data: [22.9, 10, 38.6], // ✅ your real KPI numbers
      backgroundColor: [
        "#1E90FF", // Revenue Growth (strong positive)
        "#4CAF50", // Investment Income Growth (moderate positive)
        "#1E90FF"  // Surplus Growth (strong positive)
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
      beginAtZero: false,
      min: 0,         // ✅ no negatives in your KPIs
      max: 50,        // ✅ fits 22.9%, 10%, and 38.6% nicely
      ticks: {
        stepSize: 10,
        callback: (val) => `${val}%`
      }
    }
  }
};
</script>