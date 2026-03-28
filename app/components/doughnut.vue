<template>
  <div class="lg:col-span-5 relative rounded-lg">
    <NuxtImg src="/favicon.jpeg" class="h-24 w-24 rounded-full mb-4" />
    <!-- Background accent -->
    <div class="absolute -top-4 -right-4 w-24 h-24 bg-secondary/10 -z-10"></div>

    <!-- Header -->
    <span class="text-xs text-gray-500 font-bold uppercase tracking-widest">
      Fiscal Year Total
    </span>

    <!-- Value -->
    <div class="flex items-baseline gap-2 mt-2">
      <span class="text-5xl font-bold text-[gold]">K1,211.4</span>
      <span class="text-2xl text-black">Million</span>
    </div>

    <!-- Chart -->
    <div>
      <div class="grid md:grid-cols-2 grid-cols-1">
        <div class="mt-6 w-[18em]">
          <Doughnut :data="chartData" :options="chartOptions" />
          <div class="flex items-center gap-2 text-success font-bold mt-4">
            <Icon name="material-symbols:trending-up" class="text-sm" />
            <span>+35.8% Variance</span>
          </div>
        </div>

        <!-- Growth -->

        <div class="w-full">
          <p class="text-gray-700 mt-6 max-w-7xl md:text-xl">
            Total administrative expenses increased by
            <span class="font-bold text-black">35.8%</span>, rising from
            <span class="font-bold">K891.8 million</span> in 2025 to
            <span class="font-bold">K1,211.4 million</span> in 2025/26.
            This rise was driven by inflationary pressures affecting fuel, accommodation,
            and operational costs.

            Capital expenditure amounted to
            <span class="font-bold">K4.9 million</span> (2025: K109.6 million),
            mainly for additional office equipment.

            Key expenditure movements included employee costs of
            <span class="font-bold">K222.9 million</span> (2025: K180.7m), AGM & Conference
            expenses of K202.9m, Motor Vehicle expenses of K68.9m, CPD workshop expenses of
            K149.6m (2025: K70.8m), Disciplinary Committee costs of K62.8m, Executive meetings
            at K36m, Public Interest expenses of K38m related to the 2025 Elections, and
            Garnishee expenses of <span class="font-bold">K108.7 million</span>.
          </p>
        </div>
      </div>

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

// ✅ Updated: 35.8% expense growth
const chartData = {
  labels: ['Expense Increase', 'Remaining'],
  datasets: [
    {
      data: [35.8, 64.2],
      backgroundColor: [
        '#E6C200', // gold = growth
        '#E5E7EB'  // gray = remaining
      ],
      borderWidth: 0
    }
  ]
}

const chartOptions = {
  cutout: '70%',
  plugins: {
    tooltip: {
      callbacks: {
        label: (ctx) => `${ctx.raw}%`
      }
    }
  }
}
</script>