<template>
    <div class="p-4">
      <NuxtLink to="/" class="text-sm text-gray-500 hover:underline">← Back</NuxtLink>
  
      <h2 class="text-2xl font-bold my-4">{{ review.attributes.title }}</h2>
  
      <img
        v-if="review.attributes.image?.data?.attributes?.url"
        :src="review.attributes.image.data.attributes.url"
        class="max-w-md rounded mb-4"
        alt="Review Image"
      />
  
      <p class="mb-2"><strong>Rating:</strong> {{ review.attributes.rating }}</p>
      <p class="mb-2"><strong>Author:</strong> {{ review.attributes.author }}</p>
      <p class="text-gray-700">{{ review.attributes.content }}</p>
    </div>
  </template>
  
  <script setup>
  const route = useRoute()
  const config = useRuntimeConfig()
  
  const { data } = await useFetch(`${config.public.apiBase}/reviews/${route.params.id}?populate=*`)
  const review = data.value.data
  </script>
  