<template>
  <div class="px-4 sm:px-8 py-8 sm:py-12 bg-surface text-on-surface rounded-lg">

    <!-- Description -->
    <div class="space-y-4 text-sm sm:text-base text-gray-600 mb-6">
      <p>
        <strong>Income:</strong> For 2024, income is likely to increase due to anticipated growth in membership, a
        proposed increase in membership fees, higher CLE workshop attendance, expected increased levy remittance
        from members, and improved levy recovery measures planned by the Society. We also anticipate more donor
        funding on major public interest projects undertaken by the Society.
      </p>

      <p>
        <strong>Expenses:</strong> Expenses in 2024 are expected to rise due to increased operations, higher cost
        of goods and services, staff costs, and capital expenditure (including expected expenses by the Land
        Development Committee and the purchase of the CEO’s motor vehicle). General expenses are also likely to
        increase due to inflationary pressures and overall price increases in commodities and services.
      </p>
    </div>

    <!-- Outlook Chart -->
    <div class="w-full h-64 sm:h-80 md:h-[28rem] mb-6">
      <Bar :data="chartData" :options="chartOptions" class="w-full h-full" />
    </div>

    <p class="text-gray-600 text-sm sm:text-base">
      I would like to sincerely appreciate the support you render to my office and the timely payments you make.
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

// Example data for 2024 outlook
const chartData = {
  labels: ["Income", "Expenses"],
  datasets: [
    {
      label: "2024 Projection (K Millions)",
      data: [200, 150],
      backgroundColor: ["#10B981", "#EF4444"],
      borderRadius: 8
    },
    {
      label: "2023 Actual (K Millions)",
      data: [180, 130],
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
        stepSize: 50, // ✅ makes scale cleaner: 0, 50, 100, 150, 200
        callback: (val) => `K${val}M`
      }
    }
  }
};
</script>