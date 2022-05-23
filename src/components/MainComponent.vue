<template>
  
  <main class="container-fluid">

    <div class="container d-flex flex-wrap justify-content-between">

      <CardComponent v-for="card in movieList" :key="card.id" :dataCard="card"/>
      
      <MovieComponent 
      />

      <!-- :movieList="MovieList" -->
      
    </div>
  </main>
  
</template>

<script>

import CardComponent from './CardComponent.vue';
import MovieComponent from './MovieComponent.vue';


export default {
    name: "MainComponent",

    components: { CardComponent, MovieComponent },

    props: {
      movieList: Array
    }
}
</script>

<style lang="scss" scoped>

  main {
    background-color: #111111;
    height: 100%;
    padding-top: 15px;
  }


</style>