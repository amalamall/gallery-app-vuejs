<template>
    <div class="image-grid" ref="imageGrid">
        <router-link v-for="photo in photos" :key="photo.name" :to="{ name: 'ImageDetails', params: { id: photo.id } }" class="image-container">
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
      isLoading: false,
      category : this.$route.params.name
    };
  },
  watch: {
    '$route.params.name'(newCategoryName) {
      this.category = newCategoryName;
      this.photos = []
      this.loadPhotos();
    }
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
          const { data } = await axios.get(`https://api.unsplash.com/search/photos?query=${this.category}&client_id=lebTpI4Osa9WxNrZiPtmv2bQaeFaV7r4fQgoCQ6e-88`);
          if (data.results?.length !== 0) {
            this.photos = [...this.photos, ...data.results];
            this.page++;
        }
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
  column-count: 4;
  column-gap: 10px; 
}

.image-container {
  margin: 0;
  display: inline-block;
  width: 100%;
  height: auto;
  margin-bottom: 10px;
}

.image-container img {
  max-width: 100%;
  max-height: 100%;
}

@media screen and (min-width: 768px) {
  .image-grid {
    column-width: calc(100% / 4); 
  }
}
</style>