<template>
  <div class="container">
    <div>
      <ul>
        <li v-for="(jeu, index) in jeux_video" :key="index"><NuxtLink :to="`jeu/${index}`">{{jeu.post_title}}</NuxtLink></li>
      </ul>
    </div>
  </div>
</template>

<script>

import axios from 'axios';

export default {
  name: 'homepage',
  data() {
    return {
      jeux_video : []
    }
  },
  mounted() {
    axios.get('http://sitetest.local/wp-json/wp/v2/jeux_video').then(response => (this.jeux_video = response.data))
  }
}
</script>

<style>

  :root {
    --pimary-color: #30475e;
    --secondary-color: #f05454;
    --font-color: #222831;
    --background-color: #dddddd;
  }

  body {
    margin: 0;
    padding: 0;
    background: var(--background-color); 
    font-family: sans-serif;
  }

  ul li a:link {
    text-decoration: none;
    outline: none;
  }

  ul {
    position: relative;
    width: 450px;
    margin: 100px auto 0;
    padding: 10px;
    box-sizing: border-box;
  }

  ul li {
    display: flex;
    background-color: var(--pimary-color);
    padding: 10px 20px;
    color: var(--font-color);
    margin: 5px 0;
    transition: .5s;
  }

  ul li:hover {
    transform: scale(1.1);
    background-color: var(--secondary-color);
  }
  
</style>