<template>
    <div class="px-8 py-12 bg-surface text-on-surface">
        <div>
            <h1 class="text-5xl md:text-6xl font-black text-[gold] mb-6">
                FINANCIAL POSITION
            </h1>
            <p class="text-lg md:text-xl leading-relaxed text-gray-600 mb-4">
                Excellent liquidity: Acid test ratio 26.5 (2022: 23.8)<br>
                Current assets: K408.5M (2022: K245.0M)<br>
                Current liabilities: K15.4M (2022: K10.3M)<br>
                Gearing ratio: 0 (no borrowing)
            </p>
        </div>
        <!-- Chart -->
        <Bar :data="chartData" :options="chartOptions" />

        <!-- Ratios / Highlights -->
        <!-- <div class="mt-8 grid grid-cols-1 md:grid-cols-3 gap-6">
            <div class="p-4 bg-surface-container-high rounded">
                <span class="text-gray-500 text-sm">Acid Test Ratio</span>
                <div class="text-2xl font-bold text-green-600">26.5</div>
                <div class="text-xs text-gray-400">2022: 23.8</div>
            </div>

            <div class="p-4 bg-surface-container-high rounded">
                <span class="text-gray-500 text-sm">Gearing Ratio</span>
                <div class="text-2xl font-bold text-blue-600">0</div>
                <div class="text-xs text-gray-400">No borrowing</div>
            </div>

            <div class="p-4 bg-surface-container-high rounded">
                <span class="text-gray-500 text-sm">Liquidity</span>
                <div class="text-2xl font-bold text-[gold]">Strong</div>
            </div>
        </div> -->
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
} from 'chart.js'

import { Bar } from 'vue-chartjs'

ChartJS.register(
    BarElement,
    CategoryScale,
    LinearScale,
    Tooltip,
    Legend
)

const chartData = {
    labels: ['Current Assets', 'Current Liabilities', 'Non-Current Assets'],
    datasets: [
        {
            label: '2023',
            data: [408.5, 15.4, 437.0],
            backgroundColor: ['#3B82F6', '#EF4444', '#F59E0B']
        },
        {
            label: '2022',
            data: [245.0, 10.3, 206.8],
            backgroundColor: ['#93C5FD', '#FCA5A5', '#FCD34D']
        }
    ]
}

const chartOptions = {
    responsive: true,
    plugins: {
        legend: {
            position: 'top'
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
                callback: (val) => `K${val}M`
            }
        }
    }
}
</script>
