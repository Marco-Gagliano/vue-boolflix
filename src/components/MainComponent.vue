<template>
  
  <main class="container-fluid">

    <h1>{{itemTitle}}</h1>

    <div class="movie-card container d-flex flex-nowrap">
      
      <MovieComponent v-for="(movie, i) in movieList" :key="`movie${i}`" :movie="movie"/>

      <SeriesComponent v-for="(series, i) in seriesList" :key="`series${i}`" :series="series"/>

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
    margin: 10px
  }

  main {
    background-color: #111111;
    height: 100%;
    padding-top: 15px;
  }

  .movie-card {
    overflow-x: auto;
    scrollbar-width: thin;          
    scrollbar-color: blue orange;
  }

</style>