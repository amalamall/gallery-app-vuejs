<template>
    <div class="image-details">
      <img :src="photo.urls?.regular" alt="Unsplash photo">
      <div class="details">
        <h1>{{ photo?.alt_description }}</h1>
        <p>Photo by {{ photo?.user?.name }}</p>
        <p>Download: <a :href="photo?.links?.download">Unsplash</a></p>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        photo: {}
      };
    },
    async created() {
      try {
        const response = await axios.get(`https://api.unsplash.com/photos/${this.$route.params.id}?client_id=lebTpI4Osa9WxNrZiPtmv2bQaeFaV7r4fQgoCQ6e-88`);
        this.photo = response.data;
      } catch (error) {
        console.error(error);
      }
    }
  };
  </script>
  
  <style>
  .image-details {
    max-width: 800px;
    margin: 0 auto;
  }
  
  .image-details img {
    max-width: 100%;
  }
  
  .details {
    margin-top: 20px;
  }
  
</style>  