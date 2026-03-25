<template>
  <div class="lg:col-span-5 bg-surface-container-low p-8 relative rounded-lg">
    <!-- Background accent -->
    <div class="absolute -top-4 -right-4 w-24 h-24 bg-secondary/10 -z-10"></div>

    <!-- Header -->
    <span class="text-xs text-gray-500 font-bold uppercase tracking-widest">
      Fiscal Year Total
    </span>

    <!-- Value -->
    <div class="flex items-baseline gap-2 mt-2">
      <span class="text-5xl font-bold text-[gold]">K715.1</span>
      <span class="text-2xl text-black">Million</span>
    </div>

    <!-- Chart -->
    <div class="mt-6 w-[18em]">
      <Doughnut :data="chartData" :options="chartOptions" />
    </div>

    <!-- Growth -->
    <div class="flex items-center gap-2 text-success font-bold mt-4">
      <Icon name="material-symbols:trending-up" class="text-sm" />
      <span>+22.4% Variance</span>
    </div>
  </div>
</template>

<script setup>
import {
  Chart as ChartJS,
  ArcElement,
  Tooltip
} from 'chart.js'

import { Doughnut } from 'vue-chartjs'

ChartJS.register(ArcElement, Tooltip)

// Example: show growth vs remaining (100% baseline)
const chartData = {
  labels: ['Growth', 'Remaining'],
  datasets: [
    {
      data: [22.4, 77.6],
      backgroundColor: [
        '#E6C200', // green = growth
        '#E5E7EB'  // gray = remainder
      ],
      borderWidth: 0
    }
  ]
}

const chartOptions = {
  cutout: '70%', // makes it look like a gauge
  plugins: {
    tooltip: {
      callbacks: {
        label: (ctx) => `${ctx.raw}%`
      }
    }
  }
}
</script>