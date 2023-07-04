<template>
  <div class="app">
    <WeatherWidget />
    <LocationWidget />
    <StopwatchWidget />
    <PhotoWidget />
  </div>
</template>

<script>
import WeatherWidget from './components/WeatherWidget.vue';
import LocationWidget from './components/LocationWidget.vue';
import StopwatchWidget from './components/StopwatchWidget.vue';
import PhotoWidget from './components/PhotoWidget.vue';

export default {
  components: {
    WeatherWidget,
    LocationWidget,
    StopwatchWidget,
    PhotoWidget,
  },
};
</script>

<style>
.app {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 20px;
  margin: 20px;
}
</style>

