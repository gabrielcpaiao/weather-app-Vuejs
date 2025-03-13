<template>
  <div class="weather-app">
    <h1>Weather App/Dashboard</h1>
    <div class="search-box">
      <input type="text" placeholder="Enter city name" v-model="city" @keyup.enter="fecthWeather" />
      <button @click="fetchWeather">Search</button>
    </div>
    <div v-if="Weather" class="weather-info">
      <h2>{{ weather.name }}, {{ weather.sys.country }}</h2>
      <p>{{ weather.weather[0].description }}</p>
      <p>Temperature: {{ weather.main.temp }}ºC</p>
      <p>Humidity: {{ weather.main.humidity }}%</p>
      <p>Wind Speed: {{ weather.wind.speed }} m/s</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
// import Weather from './components/weather/Weather.vue';

export default {
  data() {
    return {
      city: '',
      weather: null,
    };
  },
  methods: {
    async fetchWeather() {
      try {
        const API_KEY = 'https://api.openweathermap.org/data/2.5/weather?q=London&appid={API_KEY}&units=metric'
        const response = await axios.get(
          'https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${API_KEY}&units=metric'
        );
        this.weather = response.data;
      } catch (error) {
        console.log('Error fetching weather data: ', error);
        alert('City not found. Please try again.');
      }
    },
  },
};
</script>

<style>
.weather-app {
  text-align: center;
  padding: 20px;
}

.search-box {
  margin: 20px 0;
}

input {
  padding: 10px;
  font-size: 16px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  margin-left: 10px;
}

.weather-info {
  margin-top: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
