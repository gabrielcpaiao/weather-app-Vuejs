<template>
  <div class="weather-app">
    <h1>Weather App/Dashboard</h1>
    <div class="search-box">
      <input
      type="text"
      placeholder="Enter city name"
      v-model="city"
      @keyup.enter="fecthWeather"
      />
      <button @click="fetchWeather">Search</button>
    </div>
    <div class="weather-footer"></div>
  </div>
</template>

<script>

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
