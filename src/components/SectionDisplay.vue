<template>
    <section class="hero">
    <div class="hero-container">
      <div class="hero-content">
        <h1>Simple Gallery</h1>
        <p>
          The internet’s source of freely useable images.<br>
          Powered by creators everywhere.
        </p>
        <div class="hero-search-form">
          <form>
            <input type="text" placeholder="Search free high-resolution photos">
          </form>
        </div>
        <div class="trending-search-tags">
          <p>Trending searches: <a href="#">flower</a>, <a href="#">wallpaper</a>, <a href="#">sad</a>, <a href="#">love</a></p>
        </div>
      </div>
    </div>
    <div class="hero-overlay"></div>
  </section>
</template>

<script>
export default {
  name: "SectionDisplay",
}
</script>


<style>
    /* Hero */
.hero {
  height: 600px;
  background: url('../assets/hero.jpg') no-repeat right top;
  background-size: 100% 770px;
  width: 100%;
  position: relative;
}

.hero-overlay {
  position: absolute;
  background: rgba(0, 0, 0, 0.4);
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
}

.hero-container {
  max-width: 60%;
  margin: auto;
}

.hero-content {
  height: 600px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.hero-content h1 {
  font-size: 3rem;
  color: #fff;
  z-index: 2;
}

.hero-content p {
  color: #fff;
  z-index: 2;
  margin: 1rem 0;
  line-height: 1.5;
}

.hero-search-form {
  z-index: 2;
  margin: 1rem 0.6rem 0 0;
}

.hero-search-form input {
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