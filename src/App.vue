<template>
    <NavigationBar></NavigationBar>
</template>

<script>
import NavigationBar from "@/components/NavigationBar.vue";

export default {
  name: "App",
  components: {
    NavigationBar
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
}

body {
  font-family: "Helvetica", sans-serif;
}

ul {
  list-style: none;
}

a {
  color: #999;
  text-decoration: none;
}

/* Media queries */
@media(max-width:900px){
  .nav-search-form {
    display: none;
  }

  .hero {
    background-size: 200% 700px;
  }

  .hero-container {
    max-width: 90%;
  }

  .category-nav {
    display: none;
  }

  .images {
    margin: 0.5rem;
  }
}
</style>
