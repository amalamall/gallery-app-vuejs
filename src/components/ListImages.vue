<template>
    <div class="image-grid" ref="imageGrid">
        <router-link v-for="photo in photos" :key="photo.id" :to="{ name: 'ImageDetails', params: { id: photo.id } }" class="image-container">
        <img :src="photo.urls.regular" alt="Unsplash photo">
      </router-link>
  </div>
</template>

<script>
import axios from 'axios';
export default {
    data() {
    return {
      page: 1,
      perPage: 20,
      photos: [],
      isLoading: false
    };
  },
  created() {
    this.loadPhotos();
    window.addEventListener('scroll', this.handleScroll);
  },
  destroyed() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    async loadPhotos() {
      try {
        this.isLoading = true;
        const response = await axios.get(`https://api.unsplash.com/photos?page=${this.page}&per_page=${this.perPage}&client_id=lebTpI4Osa9WxNrZiPtmv2bQaeFaV7r4fQgoCQ6e-88`);
        this.photos = [...this.photos, ...response.data];
        this.page++;
      } catch (error) {
        console.error(error);
      } finally {
        this.isLoading = false;
      }
    },
    handleScroll() {
      const scrollPosition = window.innerHeight + window.pageYOffset;
      const pageHeight = this.$refs.imageGrid.offsetHeight;
      if (scrollPosition >= pageHeight && !this.isLoading) {
        this.loadPhotos();
      }
    }
  }


  
}
</script>



<style>
.image-grid {
  margin: 2vmin;
  column-count: 4; /* Set the number of columns */
  column-gap: 10px; /* Set the gap between columns */
}

.image-container {
  margin: 0;
  display: inline-block;
  width: 100%;
  height: auto;
  margin-bottom: 10px; /* Set the gap between rows */
}

.image-container img {
  max-width: 100%;
  max-height: 100%;
}

@media screen and (min-width: 768px) {
  .image-grid {
    column-width: calc(100% / 4); /* Set the width of each column */
  }
}
</style>