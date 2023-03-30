<template>
  <div class="not-found">
    <h1>404 Not Found</h1>
    <p>We're sorry, the page you requested could not be found.</p>
    <router-link to="/">Go back to the homepage</router-link>
  </div>
</template>

<script>
export default {
  name: 'NotFound',
};
</script>

<style scoped>
.not-found {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
}
.not-found h1 {
  font-size: 3rem;
  margin-bottom: 20px;
}
.not-found p {
  font-size: 1.2rem;
  line-height: 1.5;
  margin-bottom: 20px;
}
</style>
