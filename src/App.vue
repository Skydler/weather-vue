<script setup>
import { ref, onMounted } from "vue";
import CurrentLocation from "./components/CurrentLocationWidget.vue";

const location = ref(null);

onMounted(() => {
  navigator.geolocation.getCurrentPosition(
    (pos) => (location.value = pos.coords)
  );
});
</script>

<template>
  <h1>Weather app</h1>
  <div v-if="location !== null">
    <div>
      <CurrentLocation :location="location" />
    </div>
    <div>Future weather...</div>
  </div>
  <div v-else>Geolocation not provided :(</div>
</template>

<style>
@import "./assets/base.css";

h1 {
  text-align: center;
  padding: 20px 0px;
}

body {
  padding: 0 50px;
}
</style>
