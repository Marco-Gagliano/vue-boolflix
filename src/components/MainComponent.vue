<template>
  
  <main class="container-fluid">

    <div class="container d-flex flex-wrap justify-content-between">
      
      
      <MovieComponent v-for="(movie, i) in movieList" :key="`movie${i}`" :movie="movie"/>

      <!-- <SeriesComponent v-for="(serie, i) in seriesList" :key="`series${i}`" /> -->

    </div>
  </main>
  
</template>

<script>

import MovieComponent from './MovieComponent.vue';
// import SeriesComponent from './SeriesComponent.vue';


export default {
    name: "MainComponent",

    components: { MovieComponent },
    // components: { SeriesComponent },

    props: {
      movieList: Array,
      seriesList: Array
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