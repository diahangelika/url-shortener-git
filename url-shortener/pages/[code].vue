<template>
  <div>
    <p>Redirecting...</p>
  </div>
</template>

<script setup>
import { useRoute, navigateTo } from '#imports'

const route = useRoute()
const code = route.params.code

const { data, error } = await useFetch(`https://ee54-103-100-175-121.ngrok-free.app/api/resolve/${code}`)

if (data.value?.originalUrl) {
  navigateTo(data.value.originalUrl, { external: true })
} else {
  console.error('URL not found')
}
</script>
