<template>
    <div class="bg-surface-container-high rounded-lg">
        <div class="flex items-center gap-4 mb-4">
            <div class="h-[1px] flex-grow bg-outline-variant/30"></div>
            <span class="text-black font-manrope font-black tracking-widest uppercase">
                Key Performance Indicators
            </span>
        </div>

        <!-- Chart -->
         <div class="mt-6 w-[18em]">
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
} from 'chart.js'

import { Bar } from 'vue-chartjs'

// Register ChartJS components
ChartJS.register(
    Title,
    Tooltip,
    Legend,
    BarElement,
    CategoryScale,
    LinearScale
)

// KPI data (from your HTML)
const chartData = {
    labels: ['Revenue Growth', 'Member Compliance', 'Admin Overhead'],
    datasets: [
        {
            label: 'KPI Values (%)',
            data: [12.4, 94, -2.1],
            backgroundColor: [
                '#4CAF50', // green (positive)
                '#1E90FF', // blue (high positive)
                '#FF4C4C'  // red (negative)
            ],
            borderRadius: 6
        }
    ]
}

const chartOptions = {
    responsive: true,
    plugins: {
        legend: {
            display: false
        },
        tooltip: {
            callbacks: {
                label: (context) => `${context.raw}%`
            }
        }
    },
    scales: {
        y: {
            beginAtZero: true
        }
    }
}
</script>