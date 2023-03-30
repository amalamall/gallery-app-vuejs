<template>
<header>
    <nav class="navbar">
      <div class="left">
        <div class="logo">
          <a href="">
            <router-link :to="{ name: 'home' }"><h1>Gallery</h1></router-link>
          </a>
        </div>
        <div class="nav-search-form">
          <form>
            <input type="text" name="search" v-model="search" placeholder="Search free high-resolution photos">
            <button type="submit" @click.stop.prevent="submit()"></button>
          </form>
        </div>
      </div>
      <ul class="nav">
        <li><router-link :to="{ name: 'about' }"><a href="#">About</a></router-link>  </li>
      </ul>
    </nav>
    <div class="category-nav">
      <div class="category" v-for="category in categories" :key="category">
      <router-link :to="{ name: 'ListImagesByCollection', params: { name: category } }"><a>{{ category }}</a></router-link>
      </div>
    </div>
    <router-view></router-view> 
  </header>
  </template>
  
  <script>
  export default {
    name: "NavigationBar",
    data() {
      return {
        search : null,
        categories: ['Nature','Love','Flowers','Women']
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
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
}

.left{
    display : flex;
    align-items: center;
}

.logo a{
    color: #000;
}

.logo h1 {
    font-size:1.3rem;
}

.logo p {
    font-size:1rem;

}
.nav {
    display : flex;
    align-items: center;
}
.nav li {
    margin-right: 1.2rem;
}

.nav li a{
    font-size : 14px;
    font-weight: 550;
}

.nav li:last-child a {
    display : block;
    background: #eee;
    color : #000;
    padding: 0.5rem 0.6rem;
    border-radius: 5px;
    transition: filter 0.5s ;
}

.nav li:last-child a {
    display : block;
    background: #eee;
    color : #000;
    padding: 0.4rem 0.7rem;
    border-radius: 5px;
    transition: filter 0.5s ;
}

.nav li:last-child a:hover {
    filter : brightness(85%)
}

.nav-search-form {
    margin-left : 1rem;
}

.nav-search-form input {
    padding : 0.7rem;
    border-radius: 20px;
    border : none;
    background-color: #eee;
    width: 70vmin;
    font-size: 0.9rem;
    color:#333;
}
.nav-search-form input:focus {
 background: #fff;
}

.category-nav {
    display: flex;
    padding-left: 0.6rem;
    overflow: hidden;
}

.category-nav .category {
    padding : 0.8rem;
}

.category  a{
    font-size: 14px;
    font-weight: 500;
    letter-spacing: 1px;
    line-height: 1;
}

</style>
  