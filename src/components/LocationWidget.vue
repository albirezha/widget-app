<template>
  <div class="location-widget">
    <h2>Location</h2>
    <div v-if="loading">Loading...</div>
    <div v-else>
      <div>{{ latitude }}</div>
      <div>{{ longitude }}</div>
    </div>
  </div>
</template>

<script>
import { Geolocation } from 'vue-geolocation-api';

export default {
  data() {
    return {
      latitude: null,
      longitude: null,
      loading: true,
    };
  },
  mounted() {
    this.getLocation();
  },
  methods: {
    async getLocation() {
      try {
        const geolocation = new Geolocation();
        const position = await geolocation.getCurrentPosition();
        this.latitude = position.coords.latitude;
        this.longitude = position.coords.longitude;
        this.loading = false;
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style scoped>
.location-widget {
  text-align: center;
  margin-top: 20px;
}
</style>
