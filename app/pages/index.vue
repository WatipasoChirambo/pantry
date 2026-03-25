<template>
  <div class="min-h-screen relative overflow-hidden">

    <!-- Hero Slide Transition -->
    <transition name="keynote" mode="out-in">
      <div :key="slide" class="w-full overflow-x-hidden">

        <!-- Slide 0 – Hero -->
        <div v-if="slide === 0"
          class="relative min-h-screen overflow-x-hidden flex flex-col justify-center items-center overflow-hidden pt-20 pb-24">
          <!-- Background Motif -->
          <div class="absolute inset-0 z-0 opacity-10 pointer-events-none">
            <div
              class="absolute top-0 right-0 w-1/2 h-full bg-[radial-gradient(circle_at_center,_var(--tw-gradient-stops))] from-secondary/40 via-transparent to-transparent">
            </div>
            <img class="w-screen h-full overflow-x-hidden object-cover grayscale mix-blend-multiply"
              src="https://lh3.googleusercontent.com/aida-public/AB6AXuCbRmZ1Grz4YF1kePuzGdsDZGmUoHwKginvmyXYKhpYDkcBojg-J6Ef7dsZLs0Zal5jMCqHCrgFt6SX2KaUostQSpRTWA7zTq21rJ0u3YYxaGYwIaKX7_Y9WmpEl3SvZf-H2zrIxP1FWN2CfTz8trbK2GgPxuoQtlHvfmm7mvLm7JMMikAL5FfVs4NBk_0dEJd34xg7KymXjWX_OGm-fhf9eRMVix0jLNjOMq3_0QYAW2VPzb7gtQcQ5SHCqi9eqi7xw-CX50f0z_g"
              alt="Abstract classical marble columns" />
          </div>

          <!-- Content Canvas -->
          <div class="relative z-10 w-full md:max-w-6xl px-8">
            <div class="grid grid-cols-1 md:grid-cols-12 gap-12 items-center">
              <!-- Left Hero Content -->
              <div class="md:col-span-8 space-y-8">
                <div class="space-y-4">
                  <NuxtImg src="/favicon.jpeg" class="h-24 w-24 rounded-full" />
                  <div class="flex items-center gap-4">
                    <div class="statute-bar h-12"></div>

                    <span class="font-label text-black font-bold tracking-[0.2em] text-sm uppercase">
                      Annual Financial Review
                    </span>
                  </div>
                  <h2 class="font-headline text-[gold] text-6xl md:text-8xl font-black tracking-tighter leading-tight">
                    Treasurer's<br />Report 2024
                  </h2>
                </div>

                <div class="bg-surface-container-lowest p-8 border-l-8 border-[gold] shadow-sm max-w-2xl">
                  <p class="font-headline text-2xl text-gray-700 font-bold italic mb-2">
                    Presented by Kizito Kumwenda, Treasurer
                  </p>
                  <p class="font-body text-outline font-medium tracking-wide text-gray-400">
                    13 Months Period Ended 31st January 2025
                  </p>
                </div>

                <div class="flex gap-4 pt-4">
                  <button @click="goToSlide"
                    class="bg-gradient-to-br from-[black] to-[gold]-container text-on-[gold] px-8 py-4 font-label font-bold tracking-widest text-xs rounded-lg hover:shadow-lg transition-all active:scale-95">
                    COMMENCE PRESENTATION
                  </button>
                </div>
              </div>

              <!-- Right Visual Panel -->
              <div class="md:col-span-4 hidden md:block">
                <div class="relative aspect-[3/4] bg-surface-container-low overflow-hidden rounded-lg group">
                  <img
                    class="w-full h-full object-cover opacity-90 grayscale group-hover:grayscale-0 transition-all duration-700"
                    src="https://lh3.googleusercontent.com/aida-public/AB6AXuCi32Kerqb3FK_YYDMOA4KIfshE8virscHEfuiXhN4jq3NsYYVu3z_fuh4iqBqBtLJAdp5W_eF1NFKlTNLSpJnwFitszbcwbHPUuePy5Io-E-raTLlS6TZZ34T9xfPu-6NcBoz9sr7ZYfpwEvxE_zeXbTJJBZco1EdAemMRIWOEfw5-BBpEaBFD50hZrtnh6GOv6eop4efWC10Towous1afkYECRTwrdpNZmcgEU3FLO9pd0Xy4dwR-gxSlj3cRivKv1nSu8q4pR7o"
                    alt="Luxury law library interior" />
                  <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
                  <div class="absolute bottom-6 left-6 text-white">
                    <p class="font-headline font-bold text-xl tracking-tight">The 2024 Mandate</p>
                    <p class="font-body text-sm opacity-80">Fiscal Integrity &amp; Oversight</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Slide 1 – Funds Flow & Surplus -->
        <div v-else-if="slide === 1" class="grid grid-cols-1 lg:grid-cols-12 gap-4 md:gap-12 md:max-w-6xl mx-auto">
          <!-- Left Column -->
          <div class="lg:col-span-7 block md:flex flex-col md:gap-8">
            <!-- Surplus Highlight -->
            <div class="p-10 statute-bar relative">
              <div class="absolute top-0 right-0 p-8 opacity-5">
                <Icon name="material-symbols:trending-up" class="text-9xl text-green-500" />
              </div>
              <p class="font-manrope text-xs font-bold uppercase tracking-widest text-black mb-4">
                Annual Financial Result
              </p>
              <h3 class="text-7xl md:text-8xl font-notoSerif font-bold text-[gold] mb-2 tracking-tighter">
                K{{ surplusDisplay }}m
              </h3>
              <p class="text-xl font-manrope font-medium text-black max-w-md">
                Comprehensive surplus achieved through strategic fiscal oversight and improved revenue collection.
              </p>
            </div>

            <!-- Strategic Bullets -->
            <div class="grid grid-cols-1 md:grid-cols-2 md:gap-8 gap-4">
              <div class="bg-surface-container-low p-8">
                <Icon name="material-symbols:verified_user" class="text-black mb-4" />
                <h4 class="font-notoSerif font-bold text-xl text-[gold] mb-3">Statutory Compliance</h4>
                <p class="text-gray-500 text-sm leading-relaxed">
                  Fully compliant with <span class="font-bold text-black">section 86(2) of LELPA</span>, ensuring
                  transparency and accountability.
                </p>
              </div>
              <div class="bg-surface-container-low p-8">
                <Icon name="material-symbols:account_balance" class="text-black mb-4" />
                <h4 class="font-notoSerif font-bold text-xl text-[gold] mb-3">Stable Financial Position</h4>
                <p class="text-gray-500 text-sm leading-relaxed">
                  Resilient asset base and liquidity ratios maintained despite inflationary pressures in the domestic
                  economy.
                </p>
              </div>
            </div>
          </div>

          <!-- Right Sidebar -->
          <div class="lg:col-span-5">
            <div class="sticky top-32 space-y-8">
              <!-- Chart -->
              <div class="chart-container">
                <canvas ref="barChart"></canvas>
              </div>

              <!-- KPIs -->
              <div class="p-6 bg-surface-container-high rounded-lg">
                <div class="flex items-center gap-4 mb-4">
                  <div class="h-[1px] flex-grow bg-outline-variant/30"></div>
                  <span class="text-[black] font-manrope font-black tracking-widest text-black uppercase">
                    Key Performance Indicators
                  </span>
                </div>
                <ul class="space-y-4">
                  <li class="flex justify-between items-end">
                    <span class="text-sm font-manrope text-gray-500">Revenue Growth</span>
                    <span class="font-manrope font-bold text-[gold]">+12.4%</span>
                  </li>
                  <li class="flex justify-between items-end">
                    <span class="text-sm font-manrope text-gray-500">Member Compliance</span>
                    <span class="font-manrope font-bold text-[gold]">94%</span>
                  </li>
                  <li class="flex justify-between items-end">
                    <span class="text-sm font-manrope text-gray-500">Admin Overhead</span>
                    <span class="font-manrope font-bold text-[gold]">-2.1%</span>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>

        <!-- Slide 2 – Administrative Expenses / Detailed Layout -->
        <div v-else-if="slide === 2" class="overflow-scroll md:overflow-hidden md:max-w-6xl mx-auto p-10">

          <!-- Hero / Overview -->
          <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-start mb-24">
            <div class="lg:col-span-7">
              <div class="statute-bar mb-6">
                <span class="text-[gold] font-label font-extrabold uppercase tracking-[0.2em] text-xs">
                  Financial Disclosure 2024
                </span>
              </div>
              <h2 class="font-headline font-black text-5xl md:text-7xl text-black leading-tight tracking-tighter mb-8">
                Administrative <br />Expenses
              </h2>
              <p class="text-gray-400 text-lg max-w-xl leading-relaxed">
                Fiscal pressure remains elevated due to systemic economic shifts and the expansion of the Society's
                public interest mandates.
              </p>
            </div>

            <div class="lg:col-span-5 bg-surface-container-low p-8 relative">
              <div class="absolute -top-4 -right-4 w-24 h-24 bg-secondary/10 -z-10"></div>
              <div class="space-y-2">
                <span class="font-label text-xs text-gray-400 font-bold uppercase tracking-widest text-outline">Fiscal
                  Year
                  Total</span>
                <div class="flex items-baseline gap-2">
                  <span class="font-headline text-5xl font-bold text-[gold]">K715.1</span>
                  <span class="font-headline text-2xl font-medium text-black">Million</span>
                </div>
                <div class="flex items-center gap-2 text-success font-bold">
                  <Icon name="material-symbols:trending-up" class="text-sm text-green-600" />
                  <span>+22.4% Variance</span>
                </div>
              </div>
            </div>
          </div>

          <!-- [gold] Expenditure Drivers -->
          <section class="mb-24">
            <h3 class="font-headline text-2xl font-bold text-black mb-12 flex items-center gap-4">
              Primary Expenditure Drivers
              <div class="h-[1px] flex-grow bg-outline-variant/30"></div>
            </h3>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
              <!-- Driver Cards -->
              <div
                class="bg-surface-container-lowest p-6 border-l-2 border-secondary/20 hover:border-secondary transition-colors group">
                <Icon name="material-symbols:gavel" class="text-[gold] mb-4 block text-3xl" />
                <h4 class="font-bold text-black mb-2">Pro bono Scheme</h4>
                <p class="text-sm text-gray-600">Nationwide launch of the legal aid framework increasing
                  operational reach.</p>
              </div>
              <div
                class="bg-surface-container-lowest p-6 border-l-2 border-secondary/20 hover:border-secondary transition-colors group">
                <Icon name="material-symbols:groups" class="text-[gold] mb-4 block text-3xl" />
                <h4 class="font-bold text-black mb-2">Committee Activity</h4>
                <p class="text-sm text-gray-600">Enhanced regulatory oversight and expanded subcommittee
                  engagement cycles.</p>
              </div>
              <div
                class="bg-surface-container-lowest p-6 border-l-2 border-secondary/20 hover:border-secondary transition-colors group">
                <Icon name="material-symbols:arrow-upward" class="text-[gold] mb-4 block text-3xl" />
                <h4 class="font-bold text-black mb-2">MWK Devaluation</h4>
                <p class="text-sm text-gray-600">Impact of the Malawi Kwacha exchange rate on imported
                  materials and services.</p>
              </div>
              <div
                class="bg-surface-container-lowest p-6 border-l-2 border-secondary/20 hover:border-secondary transition-colors group">
                <Icon name="material-symbols:payments" class="text-[gold] mb-4 block text-3xl" />
                <h4 class="font-bold text-black mb-2">General Inflation</h4>
                <p class="text-sm text-gray-600">Systemic rising costs of utilities, stationery, and
                  logistical fulfillment.</p>
              </div>
            </div>
          </section>

          <!-- Detailed Breakdown (Bento Cards) -->
          <section class="mb-32">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
              <div class="lg:col-span-4 bg-[gold] text-on-[gold] p-10 flex flex-col justify-between min-h-[400px]">
                <div>
                  <h3 class="font-headline text-3xl text-black font-bold mb-6">Notable Increases</h3>
                  <p class="text-on-[gold]-container leading-relaxed text-black">
                    Specific operational areas recorded significant growth in capital deployment to meet statutory
                    obligations.
                  </p>
                </div>
                <div class="flex items-center gap-4">
                  <div class="w-12 h-12 rounded-full border border-yellow-500/40 flex items-center justify-center">
                    <Icon name="material-symbols:insights" class="text-yellow-600 text-xl" />
                  </div>
                  <span class="font-label text-xs uppercase tracking-widest font-semibold text-black">Expenditure
                    Analysis</span>
                </div>
              </div>

              <div class="lg:col-span-8 grid grid-cols-1 md:grid-cols-2 gap-8">
                <!-- Stat Cards -->
                <div
                  class="bg-surface-container-high p-8 flex flex-col justify-between hover:bg-surface-container-highest transition-all">
                  <div class="flex justify-between items-start">
                    <span class="font-label font-bold text-xs uppercase tracking-widest text-black">Personnel</span>
                    <Icon name="material-symbols:badge" class="text-outline text-2xl text-black" />
                  </div>
                  <div>
                    <span class="block font-headline text-4xl font-bold text-[gold] mt-6">K133.0M</span>
                    <span class="block text-gray-600 font-medium mt-1">Employee Costs</span>
                  </div>
                </div>
                <div
                  class="bg-surface-container-high p-8 flex flex-col justify-between hover:bg-surface-container-highest transition-all">
                  <div class="flex justify-between items-start">
                    <span class="font-label font-bold text-xs uppercase tracking-widest text-black">Events</span>
                    <UBadge color="neutral" variant="soft">
                      <Icon name="material-symbols:event-seat" class="text-outline text-sm" />
                    </UBadge>
                  </div>
                  <div>
                    <span class="block font-headline text-4xl font-bold text-[gold] mt-6">K129.3M</span>
                    <span class="block text-gray-600 font-medium mt-1">AGM Logistics</span>
                  </div>
                </div>
                <div
                  class="md:col-span-2 bg-surface-container-high p-8 flex items-center justify-between hover:bg-surface-container-highest transition-all">
                  <div>
                    <span
                      class="font-label font-bold text-xs uppercase tracking-widest text-black block mb-2">Professional
                      Development</span>
                    <span class="block font-headline text-4xl font-bold text-[gold]">K101.2M</span>
                    <span class="block text-gray-600 font-medium mt-1">CLE Workshops & Training</span>
                  </div>
                  <div class="w-20 h-20 bg-[gold]/5 rounded-full flex items-center justify-center">
                    <Icon name="material-symbols:school" class="text-[gold] text-3xl" />
                  </div>
                </div>
              </div>
            </div>
          </section>

          <!-- Contextual Image / Visual Anchor -->
          <section class="relative h-[400px] mb-24 overflow-hidden rounded-sm">
            <img alt="Law Society Office" class="w-full h-full object-cover grayscale contrast-125"
              src="https://lh3.googleusercontent.com/aida-public/AB6AXuAfupFQJI_m--cqBo7P7CBfY4p16vBewClnTQROYDm6EeRqvgymA1lzVrJ2PGi2cORWaWCKn43w8v17AMXVafidrEDBEHsBMK0XNcx1wRqMpZelafMiJnS6tDK5meVK6gds2vH4k79dqJ3x89zgChZjR-tXfMe8XgbReVtG_2iYERIgelVazsauRz19zryyfwAtfmW3sijmGzbB0SnSR1O4XaV1pRlRuVSMGdxQ9omKEgfMtKgGTx3AqLxT0LaMbNxi77rOKemfTmM" />
            <div class="absolute inset-0 bg-[gold]/60 mix-blend-multiply"></div>
            <div class="absolute inset-0 flex items-center px-12">
              <div class="max-w-2xl">
                <h4 class="font-headline text-3xl text-white font-bold mb-4 italic">
                  "Commitment to institutional excellence requires strategic allocation of our collective resources."
                </h4>
                <p class="text-on-[gold]-fixed-variant font-label text-sm uppercase tracking-[0.3em]">MLS Council
                  Statement</p>
              </div>
            </div>
          </section>

        </div>

        <!-- Slide 3 – Financial Position -->
        <div v-else-if="slide === 3" class="px-8 py-12 bg-surface text-on-surface font-body">
          <h1 class="text-5xl md:text-6xl font-black font-headline text-[gold] mb-6">FINANCIAL POSITION</h1>

          <p class="text-lg md:text-xl leading-relaxed text-gray-600 mb-4">
            Excellent liquidity: Acid test ratio 26.5 (2022: 23.8)<br>
            Current assets: K408.5M (2022: K245.0M)<br>
            Current liabilities: K15.4M (2022: K10.3M)<br>
            Gearing ratio: 0 (no borrowing)
          </p>

          <p class="text-lg md:text-xl leading-relaxed text-gray-600">
            Non-current assets increased from K206.8M to K437.0M, mainly due to land revaluation.
          </p>
        </div>

        <!-- Slide 4 – Fidelity Fund -->
        <div v-else-if="slide === 4" class="px-8 py-12 bg-surface text-on-surface font-body">
          <h1 class="text-5xl md:text-6xl font-black font-headline text-[gold] mb-6">FIDELITY FUND</h1>

          <p class="text-lg md:text-xl leading-relaxed text-gray-600">
            Contributions: K23.4M (2022: K36.6M)<br>
            Investments: K152.7M generating K22.5M income<br>
            Total fund: K196M<br>
            Loan repayment: K100M (building project)
          </p>
        </div>

        <!-- Slide 5 – 2024 Outlook -->
        <div v-else-if="slide === 5" class="px-8 py-12 bg-surface text-on-surface font-body">
          <h1 class="text-5xl md:text-6xl font-black font-headline text-[gold] mb-6">2024 OUTLOOK</h1>

          <div class="space-y-6 text-lg md:text-xl leading-relaxed text-gray-600">
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

            <p>
              I would like to sincerely appreciate the support you render to my office and the timely payments you make.
            </p>
          </div>
        </div>

      </div>
    </transition>

    <!-- Side Buttons -->
    <button @click="prevSlide"
      class="fixed left-4 bottom-5 -translate-y-1/2 bg-gray-800/60 hover:bg-gray-800/80 px-6 py-4 rounded-full text-black shadow-2xl text-2xl transition-all">
      ‹ Previous
    </button>
    <button @click="nextSlide"
      class="fixed right-4 bottom-5 -translate-y-1/2 bg-yellow-500 hover:bg-yellow-400 px-6 py-4 rounded-full text-black shadow-2xl text-2xl transition-all">
      Next ›
    </button>

  </div>
</template>

<script setup>
import { ref, onMounted, watch, nextTick } from 'vue'
import Chart from 'chart.js/auto'

// ------------------------
// Slide Control
// ------------------------
const slide = ref(0)
const totalSlides = 6
const nextSlide = () => slide.value = (slide.value + 1) % totalSlides
const prevSlide = () => slide.value = (slide.value - 1 + totalSlides) % totalSlides
const goToSlide = () => slide.value = 1

// ------------------------
// Animated Counters
// ------------------------
const surplusDisplay = ref(0)
const surplusTarget = 151.1

const animateCounter = (display, target) => {
  let start = 0
  const step = () => {
    start += target / 60
    if (start < target) {
      display.value = start.toFixed(1)
      requestAnimationFrame(step)
    } else {
      display.value = target
    }
  }
  step()
}

// Initialize counters on mount
onMounted(() => {
  if (slide.value === 1) animateCounter(surplusDisplay, surplusTarget)
})

// Watch for Slide 1 to trigger counter animation
watch(slide, (newVal) => {
  if (newVal === 1) {
    animateCounter(surplusDisplay, surplusTarget)
  }
})

// ------------------------
// Chart.js Setup
// ------------------------
const barChart = ref(null)
let chartInstance = null

const labels = ['Membership', 'Levy on Fees', 'CLE Workshops', 'Investments']
const chartData = {
  labels,
  datasets: [{
    label: 'Revenue Sources (K Million)',
    data: [400, 250, 300, 41.5],
    backgroundColor: ['#FACC15', '#F59E0B', '#D97706', '#B45309'],
    borderColor: ['#F59E0B', '#D97706', '#B45309', '#92400E'],
    borderWidth: 1
  }]
}

const chartConfig = {
  type: 'bar',
  data: chartData,
  options: {
    responsive: true,
    plugins: {
      legend: { position: 'bottom', labels: { color: '#000' } },
      tooltip: { callbacks: { label: ctx => `K${ctx.raw}M` } }
    },
    scales: {
      y: { beginAtZero: true, ticks: { color: '#000' } },
      x: { ticks: { color: '#000' } }
    }
  }
}

// Render Chart when Slide 1 mounts
const renderChart = async () => {
  await nextTick()
  if (barChart.value && !chartInstance) {
    chartInstance = new Chart(barChart.value, chartConfig)
  }
}

// Watch for slide changes to render chart on Slide 1
watch(slide, (newVal) => {
  if (newVal === 1) renderChart()
})

</script>