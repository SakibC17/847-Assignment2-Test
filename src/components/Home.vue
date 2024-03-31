<script setup>
import { format, compareAsc } from "date-fns";

defineProps({
  msg: {
    type: String,
    required: true
  },
  dates: {
    type: Date,
    required: true
  },
  weather: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h2>
      The date & time is {{dates}}
    </h2>
    <h2>
      The weather in Belleville, Ontario is {{weather}} °C.
    </h2>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 3rem;
  position: relative;
  top: -10px;
}

h2 {
  font-size: 2rem;
  margin-top: 20px;
}
/* 
.greetings h1,
.greetings h2 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h2 {
    text-align: left;
  }
} */
</style>