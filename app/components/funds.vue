<template>
    <div class="px-4 sm:px-8 py-8 sm:py-12 bg-surface text-on-surface rounded-lg">
        <div>
            <h1 class="text-3xl sm:text-5xl font-black text-[gold] mb-4 sm:mb-6">
                FIDELITY FUND
            </h1>
            <p class="mb-4 text-gray-500 text-sm sm:text-base">
                The Society received a total sum of K23.4 million (2022: K36.6 million) contribution towards the
                fidelity fund. A total of K152.7 million was invested with the Old Mutual Unit Trust and generating a
                finance income of K22.5 million. Fidelity fund has a total sum of K196 million. An amount of K100
                million which the Malawi Law Society borrowed last year to finance the building project was repaid
                during the year under review with an interest.
            </p>
        </div>
        <!-- Highlights -->
        <div class="mt-6 flex md:grid grid-cols-1 sm:grid-cols-3 gap-4">
            <div class="p-4 bg-surface-container-high rounded">
                <span class="text-gray-500 text-xs sm:text-sm">Total Fund</span>
                <div class="text-xl sm:text-2xl font-bold text-[gold]">K196M</div>
            </div>

            <div class="p-4 bg-surface-container-high rounded">
                <span class="text-gray-500 text-xs sm:text-sm">Investment Income</span>
                <div class="text-xl sm:text-2xl font-bold text-green-600">K22.5M</div>
            </div>

            <div class="p-4 bg-surface-container-high rounded">
                <span class="text-gray-500 text-xs sm:text-sm">Loan Repayment</span>
                <div class="text-xl sm:text-2xl font-bold text-red-500">K100M</div>
            </div>
        </div>
        <!-- Main Chart -->
        <div class="mt-6 w-full sm:w-[24rem]">
            <Bar :data="chartData" :options="chartOptions" />
        </div>
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
    labels: ['Contributions', 'Investments', 'Income', 'Loan Repayment'],
    datasets: [
        {
            label: '2023 (K Millions)',
            data: [23.4, 152.7, 22.5, 100],
            backgroundColor: ['#3B82F6', '#10B981', '#F59E0B', '#EF4444'],
            borderRadius: 8
        },
        {
            label: '2022 (K Millions)',
            data: [36.6, 0, 0, 0],
            backgroundColor: ['#93C5FD', '#D1FAE5', '#FCD34D', '#FCA5A5'],
            borderRadius: 8
        }
    ]
}

const chartOptions = {
    responsive: true,
    maintainAspectRatio: false,
    plugins: {
        legend: {
            position: 'top',
            labels: {
                boxWidth: 15,
                padding: 10
            }
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
