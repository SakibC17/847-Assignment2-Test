<script setup>
import { RouterLink, RouterView, useRoute } from 'vue-router'
import Home from './components/Home.vue'
import { format, compareAsc } from "date-fns";
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
  <header>
    <div class="wrapper">
      <RouterView />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About Us</RouterLink>
        <RouterLink to="/services">Our Services</RouterLink>
        <RouterLink to="/customer">Our Customers</RouterLink>
      </nav>
    </div>
  </header>
 
</template>

<style scoped>
 header {
  line-height: 1.5;
  max-height: 100vh; 
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
} 


header .wrapper {
  display: flex;
  place-items: flex-start;
  flex-wrap: wrap;
}

nav {
  text-align: left;
  margin-left: -1rem;
  font-size: 1rem;

  padding: 1rem 0;
  margin-top: 1rem;
}

</style>
