<template>
  <div class="lg:col-span-8 bg-surface-container-high p-8 rounded-lg">
    <!-- Header -->
    <div class="flex items-center gap-4 mb-6">
      <div class="h-[1px] flex-grow bg-outline-variant/30"></div>
      <span class="text-black font-bold tracking-widest uppercase text-xs">
        Budget Distribution
      </span>
    </div>

    <!-- Responsive Chart -->
    <div class="w-full h-64 sm:h-72 md:h-96">
      <Bar :data="chartData" :options="chartOptions" class="w-full h-full" />
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

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
);

const props = defineProps({
  cards: {
    type: Array,
    default: () => [
      {
        title: "Personnel",
        value: "K133.0M",
        subtitle: "Employee Costs"
      },
      {
        title: "Events",
        value: "K129.3M",
        subtitle: "AGM Logistics"
      },
      {
        title: "Professional Development",
        value: "K101.2M",
        subtitle: "CLE Workshops & Training"
      }
    ]
  }
});

// Convert "K133.0M" → 133
const parseValue = (val) => {
  return parseFloat(val.replace(/[^0-9.]/g, ""));
};

const chartData = {
  labels: props.cards.map((c) => c.title),
  datasets: [
    {
      label: "Amount (Millions)",
      data: props.cards.map((c) => parseValue(c.value)),
      backgroundColor: ["#3B82F6", "#10B981", "#F59E0B"],
      borderRadius: 8
    }
  ]
};

const chartOptions = {
  responsive: true,
  maintainAspectRatio: false, // ✅ allows height to be controlled by parent
  plugins: {
    legend: {
      display: false
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
        callback: (value) => `K${value}M`
      }
    }
  }
};
</script>