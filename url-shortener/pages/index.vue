
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
      <a :href="shortUrl" target="_blank">URL</a>
    </div>
  </div>
</template>

<script setup>
// import { ref } from 'vue'

// const longUrl = ref('')
// const shortUrl = ref('')

// const shortenUrl = async () => {
//   const { data, error } = await useFetch('http://localhost:8000/api/shorten', {
//     method: 'POST',
//     body: { url: longUrl.value },
//   })

//   if (error.value) {
//     alert('Failed to shorten URL')
//   } else {
//     shortUrl.value = data.value.short_url
//   }
// }
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
