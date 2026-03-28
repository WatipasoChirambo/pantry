<script setup>
useHead({
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ],
  link: [
    { rel: 'icon', href: '/favicon.jpg' }
  ],
  htmlAttrs: {
    lang: 'en'
  }
})

const title = 'Malawi Law Society - 2025 Financial Performance Review'
const description = 'A comprehensive review of the Malawi Law Society’s 2025 financial performance, highlighting revenue trends, expenditure movements, liquidity position, investment outcomes, and the overall fiscal health of the Society.'

useSeoMeta({
  title,
  description,
  ogTitle: title,
  ogDescription: description,
  ogImage: '/favicon.jpg',
  twitterImage: '/favicon.jpg',
  twitterCard: 'summary_large_image'
})
</script>

<template>
  <div class="bg-white w-full overflow-x-hidden md:overflow-x-hidden in-h-screen">
<NuxtPage />
  </div>
    
</template>
