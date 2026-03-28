<template>
  <div class="px-4 sm:px-8 py-8 sm:py-12 bg-surface text-on-surface rounded-lg">

    <!-- Description -->
    <div class="space-y-4 text-sm sm:text-base text-gray-600 mb-6">

      <p>
        <strong>Income:</strong> For 2025, income is projected to increase due to anticipated growth in membership,
        the proposed increase in membership fees, higher CPD workshop attendance, improved compliance in levy
        remittance from members, and strengthened levy recovery measures to be implemented by the Society. 
        Additional growth is expected from donor funding towards major public interest projects currently underway.
      </p>

      <p>
        <strong>Expenses:</strong> Expenses in 2025 are expected to rise due to an increase in the Society’s operational
        activities, higher costs of goods and services, rising staff costs, and planned capital expenditure. 
        This includes expenditures by the Land Development Committee and the purchase of a motor vehicle to 
        reduce long‑term maintenance costs. General expenses are also expected to increase as a result of 
        inflationary pressures and the overall rise in commodity and service prices.
      </p>

    </div>

    <!-- Outlook Chart -->
    <div class="w-full h-64 sm:h-80 md:h-[28rem] mb-6">
      <Bar :data="chartData" :options="chartOptions" class="w-full h-full" />
    </div>

    <p class="text-gray-600 text-sm sm:text-base">
      I would like to appreciate the support you render to my office and the payments that you make.
    </p>

  </div>
</template>

<script setup>
import {
  Chart as ChartJS,
  BarElement,
  CategoryScale,
  LinearScale,
  Tooltip,
  Legend
} from "chart.js";

import { Bar } from "vue-chartjs";

ChartJS.register(BarElement, CategoryScale, LinearScale, Tooltip, Legend);

// Example data for 2025 outlook (you may adjust values)
const chartData = {
  labels: ["Income", "Expenses"],
  datasets: [
    {
      label: "2025 Projection (K Millions)",
      data: [230, 180], // ✅ Adjust if needed
      backgroundColor: ["#10B981", "#EF4444"],
      borderRadius: 8
    },
    {
      label: "2024 Actual (K Millions)",
      data: [200, 150],
      backgroundColor: ["#93C5FD", "#FCA5A5"],
      borderRadius: 8
    }
  ]
};

const chartOptions = {
  responsive: true,
  maintainAspectRatio: false,
  plugins: {
    legend: {
      position: "top"
    },
    tooltip: {
      callbacks: {
        label: (ctx) => `K${ctx.raw}M`
      }
    }
  },
  scales: {
    y: {
      beginAtZero: true,
      ticks: {
        stepSize: 50,
        callback: (val) => `K${val}M`
      }
    }
  }
};
</script>