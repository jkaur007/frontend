<template>
    <div class="container">
      <NuxtLink to="/">← Back</NuxtLink>
      <div v-if="review">
        <h1>{{ review.title }}</h1>
        <img :src="review.poster" alt="Poster" style="max-width: 300px;" />
        <p><strong>Rating:</strong> {{ review.rating }}</p>
        <p><strong>Date:</strong> {{ review.date }}</p>
        <p><strong>Category:</strong> {{ review.category }}</p>
        <p>{{ review.body }}</p>
      </div>
    </div>
  </template>
  
  <script setup>
  const { slug } = useRoute().params
  const { data: reviews } = await useFetch('/data/reviews.json')
  const review = computed(() => reviews.value.find(r => r.slug === slug))
  </script>
  