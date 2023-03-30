<template>
    <section class="bg">
    <div class="bg-container">
      <div class="bg-content">
        <h1>Simple Gallery</h1>
        <p>
          The internet’s source of freely useable images.<br>
          Powered by creators everywhere.
        </p>
        <div class="bg-search-form">
          <form>
            <input type="text" name="search" v-model="search" placeholder="Search free high-resolution photos">
            <button type="submit" @click.stop.prevent="submit()"></button>
          </form>
        </div>
        <div class="trending-search-tags">
          <p>
            Trending searches: 
            <a v-for="category in categories" :key="category" href="#">
              <router-link :to="{ name: 'ListImagesByCollection', params: { name: category } }">
                {{ category }}
              </router-link>
            </a>
              </p>
        </div>
      </div>
    </div>
    <div class="bg-overlay"></div>
  </section>
</template>

<script>
export default {
  name: "SectionDisplay",
  data() {
      return {
        search : null,
        categories: ['flower','wallpaper','sad','love']
      };
    },
  methods :{
    submit(){
      this.$router.push("/images/collection/"+ this.search);
    }
  }
}
</script>


<style>
    /* bg */
.bg {
  height: 600px;
  background: url('../assets/bg-gallery.jpg') no-repeat right top;
  background-size: 100% 770px;
  width: 100%;
  position: relative;
}

.bg-overlay {
  position: absolute;
  background: rgba(0, 0, 0, 0.5);
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
}

.bg-container {
  max-width: 60%;
  margin: auto;
}

.bg-content {
  height: 600px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.bg-content h1 {
  font-size: 3rem;
  color: #fff;
  z-index: 2;
}

.bg-content p {
  color: #fff;
  z-index: 2;
  margin: 1rem 0;
  line-height: 1.5;
}

.bg-search-form {
  z-index: 2;
  margin: 1rem 0.6rem 0 0;
}

.bg-search-form input {
  width: 100%;
  padding: 1.2rem;
  border-radius: 5px;
  border: none;
  color: #000;
  font-size: 0.9rem;
}

.trending-search-tags {
  z-index: 2;
}

.trending-search-tags a {
  color: #999;
  transition: 0.5s color;
}

.trending-search-tags a:hover {
  color: #fff;
}
</style>