<template>
  <div>
    <div class="single-image">
      <div class="image-details">
      <img :src="photo.urls?.regular" alt="Unsplash photo">
      <div class="details">
        <h1>{{ photo?.alt_description }}</h1>
        <p>Photo by {{ photo?.user?.name }}</p>
        <p>Download: <a :href="photo?.links?.download">Unsplash</a></p>
      </div>
      </div>
    </div>
  </div>

  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        photo: {},
        selectedPhoto: {},
        showDetails: false,
      };
    },
    async created() {
      try {
        const response = await axios.get(`https://api.unsplash.com/photos/${this.$route.params.id}?client_id=lebTpI4Osa9WxNrZiPtmv2bQaeFaV7r4fQgoCQ6e-88`);
        this.photo = response.data;
      } catch (error) {
        console.error(error);
      }
    },
    methods:{
    }
  };
  </script>
  
  <style>

.single-image {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .image-details {
    position: relative;
    max-width: 800px;
    margin: 0 auto;
  }

  .image-details img {
    max-width: 100%;
  }

  .details {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: white;
    text-shadow: 0px 0px 5px rgba(0,0,0,0.5);
    background-color: rgba(0,0,0,0.5);
    padding: 20px;
    box-sizing: border-box;
  }

  .details h1 {
    font-size: 36px;
    margin-bottom: 10px;
    text-align: center;
  }

  .details p {
    font-size: 20px;
    margin: 10px 0;
    text-align: center;
  }

  .details a {
    color: white;
    text-decoration: underline;
  }
  
  
</style>  