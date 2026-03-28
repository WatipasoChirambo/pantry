<template>
  <div class="px-4 sm:px-8 py-8 sm:py-12 bg-surface text-on-surface rounded-lg">
    <!-- Header & Description -->
    <div>
      <h1 class="text-3xl sm:text-5xl font-black text-[gold] mb-4 sm:mb-6">
        FIDELITY FUND
      </h1>

      <p class="mb-4 text-gray-500 text-sm sm:text-base">
        The Society received a total sum of <strong>K51.9 million</strong> (2025: K47.5 million) 
        towards the Fidelity Fund. A total of <strong>K283.7 million</strong> was invested with 
        the Old Mutual Unit Trust, generating a finance income of <strong>K57.8 million</strong>. 
        The Fidelity Fund now holds a total sum of <strong>K393.3 million</strong>.
      </p>
    </div>

    <!-- NEW KPI ROW -->
    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 mt-8 mb-8">
      <div class="bg-surface-container-high rounded p-4">
        <p class="text-xs text-gray-500 uppercase">Contribution Growth</p>
        <p class="text-2xl font-bold text-green-600">
          +{{ contributionGrowthDisplay }}%
        </p>
      </div>

      <div class="bg-surface-container-high rounded p-4">
        <p class="text-xs text-gray-500 uppercase">Investment Income Growth</p>
        <p class="text-2xl font-bold text-green-600">
          +{{ incomeGrowthDisplay }}%
        </p>
      </div>

      <div class="bg-surface-container-high rounded p-4">
        <p class="text-xs text-gray-500 uppercase">Fund Growth</p>
        <p class="text-2xl font-bold text-green-600">
          +{{ fundGrowthDisplay }}%
        </p>
      </div>
    </div>

    <!-- Highlights -->
    <div class="mt-6 flex gap-4 flex-wrap">
      <div class="p-4 bg-surface-container-high rounded">
        <span class="text-gray-500 text-xs sm:text-sm">Total Fund</span>
        <div class="text-xl sm:text-2xl font-bold text-[gold]">
          K{{ totalFundDisplay }}M
        </div>
      </div>

      <div class="p-4 bg-surface-container-high rounded">
        <span class="text-gray-500 text-xs sm:text-sm">Investment Income</span>
        <div class="text-xl sm:text-2xl font-bold text-green-600">
          K{{ incomeDisplay }}M
        </div>
      </div>

      <div class="p-4 bg-surface-container-high rounded">
        <span class="text-gray-500 text-xs sm:text-sm">Annual Contributions</span>
        <div class="text-xl sm:text-2xl font-bold text-blue-600">
          K{{ contributionDisplay }}M
        </div>
      </div>
    </div>

    <!-- Responsive Chart -->
    <div class="mt-6 w-full h-64 sm:h-80 md:h-[28rem]">
      <Bar :data="chartData" :options="chartOptions" class="w-full h-full" />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
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

/* ✅ Simple animation utility */
function useCounter(target, speed = 20) {
  const value = ref(0);
  onMounted(() => {
    const update = () => {
      if (value.value < target) {
        value.value += Math.ceil(target / speed);
        requestAnimationFrame(update);
      } else {
        value.value = target;
      }
    };
    update();
  });
  return value;
}

/* ✅ Animated KPI values */
const totalFundDisplay = useCounter(393.3);
const incomeDisplay = useCounter(57.8);
const contributionDisplay = useCounter(51.9);

/* ✅ KPI Growth Rates */
const contributionGrowthDisplay = useCounter(
  (((51.9 - 47.5) / 47.5) * 100).toFixed(1)
);
const incomeGrowthDisplay = useCounter(
  (((57.8 - 22.5) / 22.5) * 100).toFixed(1)
);
const fundGrowthDisplay = useCounter(
  (((393.3 - 196) / 196) * 100).toFixed(1)
);

/* ✅ Updated Chart Data */
const chartData = {
  labels: ["Contributions", "Investments", "Income"],
  datasets: [
    {
      label: "2025 (K Millions)",
      data: [51.9, 283.7, 57.8],
      backgroundColor: ["#3B82F6", "#10B981", "#F59E0B"],
      borderRadius: 8
    },
    {
      label: "2024 (K Millions)",
      data: [47.5, 0, 0],
      backgroundColor: ["#93C5FD", "#D1FAE5", "#FCD34D"],
      borderRadius: 8
    }
  ]
};

const chartOptions = {
  responsive: true,
  maintainAspectRatio: false,
  plugins: {
    legend: {
      position: "top",
      labels: { boxWidth: 15, padding: 10 }
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