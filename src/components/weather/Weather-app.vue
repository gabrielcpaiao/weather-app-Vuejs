<template>
    <div class="weather-container">
        <h2>Weather Dashboard</h2>
        <input v-model="city" placeholder="Enter city name" />
        <button @click="getWeather">Search</button>

        <div v-if="weather">
            <h3>{{ weather.name }}</h3>
            <p>Temperature: {{ weather.main.temp }}°C</p>
            <p>Humidity: {{ weather.main.humidity }}%</p>
            <p>Condition: {{ weather.weather[0].description }}</p>
            <img :src="iconUrl" alt="Weather Icon" />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            city: "London", // Default city
            weather: null
        };
    },
    computed: {
        iconUrl() {
            if (this.weather) {
                return `https://openweathermap.org/img/wn/${this.weather.weather[0].icon}@2x.png`;
            }
            return "";
        }
    },
    methods: {
        async getWeather() {
            const apiKey = "8f99d3e84c8fcc96c65bcee0812bf8fc"; // Replace with your key
            const url = `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${apiKey}&units=metric`;

            try {
                const response = await fetch(url);
                const data = await response.json();
                this.weather = data;
            } catch (error) {
                console.error("Error fetching weather data:", error);
            }
        }
    }
};
</script>

<style scoped>
.weather-container {
    text-align: center;
    margin-top: 20px;
}
input {
    padding: 5px;
    margin-right: 10px;
}
button {
    padding: 5px 10px;
    cursor: pointer;
}
</style>
