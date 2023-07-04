<template>
    <div class="weather-widget">
      <h2>{{ city }}</h2>
      <div v-if="loading">Loading...</div>
      <div v-else>
        <div>{{ temperature }}°C</div>
        <div>{{ description }}</div>
        <div>{{ humidity }}% Humidity</div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        city: 'Jakarta',
        temperature: null,
        description: null,
        humidity: null,
        loading: true,
      };
    },
    mounted() {
      this.getWeatherData();
    },
    methods: {
      async getWeatherData() {
        try {
          const response = await axios.get(
            `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=4b93401745642381b273943dd958d0ad&units=metric`
          );
          const data = response.data;
          this.temperature = data.main.temp;
          this.description = data.weather[0].description;
          this.humidity = data.main.humidity;
          this.loading = false;
        } catch (error) {
          console.error(error);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .weather-widget {
    text-align: center;
    margin-top: 20px;
  }
  </style>
  