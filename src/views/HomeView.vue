<script setup>
import Home from '../components/Home.vue'
import { format } from "date-fns";
import { ref, watchEffect } from 'vue'

const date = format(new Date(), "MM/dd/yyyy hh:mm:ss");
const API_URL = `https://api.openweathermap.org/data/2.5/weather?q=`;
const cityCountry = 'Belleville,ca';
const API_KEY = '&appid=0dac45f986747aaa0880a63fbf028b9a';
const units = '&units=metric'
const commits = ref(null)

watchEffect(async () => {
  const url = `${API_URL}${cityCountry}${API_KEY}${units}`
  commits.value = await (await fetch(url)).json()
})

</script>

<template>
  <main>
    <Home msg="Home Page - Group 36" :dates="date" :weather="commits.main.temp"/>
  </main>
</template>
