
<template>
  <div class="container">
    <h1>Simple URL Shortener</h1>
    <input v-model="longUrl" placeholder="Paste your long URL" />
    <button @click="shortenUrl">Shorten</button>

    <div class="hasil">
      <h4>TADAM JADI PENDEK : </h4>
    </div>

    <div v-if="shortUrl">
      <p>Short URL:</p>
      <a :href="shortUrl" target="_blank">{{ shortUrl }}</a>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const longUrl = ref('')
const shortUrl = ref('')

const shortenUrl = async () => {
  if (!longUrl.value) {
    alert('Please enter a URL')
    return
  }

  const { data, error } = await useFetch('https://ee54-103-100-175-121.ngrok-free.app/api/shorten', {
    method: 'POST',
    body: { originalUrl: longUrl.value },
    headers: {
      'Content-Type': 'application/json'
    }
  })

  if (error.value || !data.value?.shortUrl) {
    alert('Failed to shorten URL')
  } else {
    shortUrl.value = data.value.shortUrl
  }
}
</script>



<style scoped>
.container {
  max-width: 600px;
  margin: 2rem auto;
  text-align: center;
}
input {
  width: 80%;
  padding: 10px;
  margin-bottom: 1rem;
}
button {
  padding: 10px 20px;
}
</style>
