<template>
    <div class="container">
      <h1>Movie Reviews</h1>
      <input v-model="search" placeholder="Search reviews..." class="form-control my-3" />
  
      <div v-for="review in filteredReviews" :key="review.id">
        <NuxtLink :to="`/review/${review.slug}`">
          <h2>{{ review.title }}</h2>
          <p>{{ review.short_description }}</p>
        </NuxtLink>
      </div>
    </div>
  </template>
  
  <script setup>
  const search = ref("")
  const { data: reviews } = await useFetch('/data/reviews.json')
  
  const filteredReviews = computed(() =>
    reviews.value.filter(review =>
      review.title.toLowerCase().includes(search.value.toLowerCase())
    )
  )
  </script>
  
