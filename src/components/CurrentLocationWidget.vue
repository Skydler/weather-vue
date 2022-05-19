<script setup>
import { ref, onBeforeMount } from "vue";
const props = defineProps(["location"]);

const weatherData = ref({
  location: {
    name: "Berazategui",
    region: "Buenos Aires",
    country: "Argentina",
    lat: -34.72,
    lon: -58.22,
    tz_id: "America/Montevideo",
    localtime_epoch: 1652990851,
    localtime: "2022-05-19 17:07",
  },
  current: {
    last_updated_epoch: 1652986800,
    last_updated: "2022-05-19 16:00",
    temp_c: 15,
    temp_f: 59,
    is_day: 1,
    condition: {
      text: "Sunny",
      icon: "//cdn.weatherapi.com/weather/64x64/day/113.png",
      code: 1000,
    },
    wind_mph: 2.5,
    wind_kph: 4,
    wind_degree: 90,
    wind_dir: "E",
    pressure_mb: 1019,
    pressure_in: 30.09,
    precip_mm: 0,
    precip_in: 0,
    humidity: 55,
    cloud: 0,
    feelslike_c: 14.8,
    feelslike_f: 58.7,
    vis_km: 7,
    vis_miles: 4,
    uv: 5,
    gust_mph: 5.8,
    gust_kph: 9.4,
  },
});

// onBeforeMount(() => {
//   let key = import.meta.env.VITE_WEATHER_API_KEY;
//   let url = `http://api.weatherapi.com/v1/current.json?key=${key}&q=${props.location.latitude},${props.location.longitude}`;
//   fetch(url)
//     .then((res) => res.json())
//     .then((data) => (weatherData.value = data));
// });
</script>

<template>
  <div v-if="weatherData" class="card">
    <h4 class="card-title">
      Current location: {{ weatherData.location.name }},
      {{ weatherData.location.region }}
      <img
        class="weather-icon"
        :src="weatherData.current.condition.icon"
        width="64"
        height="64"
      />
    </h4>
    <div class="card-body">
      <small>Last updated: {{ weatherData.current.last_updated }}</small>
      <p>
        {{ weatherData.current.condition.text }}:
        <span>{{ weatherData.current.temp_c }} Cº</span>
      </p>
    </div>
  </div>
</template>

<style>
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  max-width: 500px;
  padding: 10px;
}

.card-title {
}

.card-body {
  display: flex;
  flex-direction: column;
}

img.weather-icon {
  float: right;
}

small {
  font-size: 0.6rem;
}
</style>
