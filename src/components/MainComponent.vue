<template>
  
  <main class="container-fluid">

    <h1 class="text-uppercase">{{itemTitle}}</h1>

    <div class="movie-card container d-flex flex-nowrap">
      <MovieComponent v-for="movie in movieList" :key="movie.id" :movie="movie"/>
    </div>

    <div class="series-card container d-flex flex-nowrap">
      <SeriesComponent v-for="series in seriesList" :key="series.id" :series="series"/>
    </div>
    
  </main>
  
</template>


<script>

import MovieComponent from './MovieComponent.vue';
import SeriesComponent from './SeriesComponent.vue';

export default {
    name: "MainComponent",

    components: { MovieComponent, SeriesComponent },

    props: {
      movieList: Array,
      seriesList: Array,
      itemTitle: String
    }
}

</script>


<style lang="scss" scoped>

  h1 {
    margin: 10px;
    color: #FF1111
  }

  main {
    background-color: #111111;
    height: 100%;
    padding-top: 15px;
  }

  .movie-card, .series-card {
    overflow-x: auto;
  }

  .series-card {
    margin-bottom: 50px
  }
  
</style>