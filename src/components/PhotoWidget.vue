<template>
  <div class="photo-widget">
    <h2>Photo</h2>
    <div v-if="loading">Loading...</div>
    <div v-else>
      <img :src="photoUrl" alt="Random Photo" />
      <button @click="getRandomPhoto">Get Random Photo</button>
    </div>
  </div>
</template>

<script>
import PictureInput from 'vue-picture-input';

export default {
  data() {
    return {
      photoUrl: null,
      loading: true,
    };
  },
  mounted() {
    this.getRandomPhoto();
  },
  methods: {
    getRandomPhoto() {
      // Simulating fetching a random photo URL
      setTimeout(() => {
        this.photoUrl = 'https://via.placeholder.com/400';
        this.loading = false;
      }, 1000);
    },
  },
  components: {
    PictureInput,
  },
};
</script>

<style scoped>
.photo-widget {
  text-align: center;
  margin-top: 20px;
}

.photo-widget img {
  max-width: 100%;
}
</style>
