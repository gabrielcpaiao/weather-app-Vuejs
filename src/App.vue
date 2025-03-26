<template>
    <div>
        <Weather />
    </div>
</template>

<script>
import WeatherApp from "./components/weather/Weather-app.vue";

export default {
    components: {
        Weather: WeatherApp
    }
};
</script>
