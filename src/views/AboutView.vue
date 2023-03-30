<template>
  <div class="about">
    <h1>About Us</h1>
    <p>We are a team of passionate photographers who want to share our love of photography with the world. Our goal is to showcase the beauty of the world through our images.</p>
    <p>We use the Unsplash API to source our images. Unsplash is a platform that allows photographers to share their work with the world and for people to use those images for free.</p>
    <p>If you're interested in using any of the images you see on our site, feel free to download them from Unsplash. All images on Unsplash are free to use for personal and commercial purposes.</p>
  </div>
</template>

<script>
export default {
  name: 'AboutView',
};
</script>

<style scoped>
.about {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}
.about h1 {
  font-size: 2.5rem;
  margin-bottom: 20px;
}
.about p {
  font-size: 1.2rem;
  line-height: 1.5;
  margin-bottom: 20px;
}
</style>