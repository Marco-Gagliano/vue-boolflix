<template>
  <div id="app">
    
    <HeaderComponent @startSearch="textToSearch"/>

    <!-- <div class="container" v-if="loadingPage"></div> -->

    <!-- utilizzo del v-else if (?)in cui se la "nome array == 0" inserire un messaggio dentro un h4-->

    <!-- <div v-else>
      <span class="loader"></span>
    </div> -->

    <MainComponent :movieList="movieList" :seriesList="seriesList"/>

  </div>
</template>

<script>

import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent,
  },

  data() {
    return {
      apiURLMovie: "https://api.themoviedb.org/3/search/movie",
      apiParamsMovie: {
        api_key: "6bb3bf68889e21ad45904086318351a4",
        language: "it-IT",
        query: "",
      },
      movieList: [],

      apiURLSeries: "https://api.themoviedb.org/3/search/tv",
      apiParamsSeries: {
        api_key: "6bb3bf68889e21ad45904086318351a4",
        language: "it-IT",
        query: "",
      },
      seriesList: [],
      // loadingPage: true,
    }
  },

  methods: {

    getApiMovie(){
      axios.get(this.apiURLMovie, {
        params: this.apiParamsMovie
      })

      .then(res => {
        // console.log(res.data);
        this.movieList = res.data.results;
      })

      .catch(err => {
        console.log(err);
      })
    },

    getApiSeries(){
      axios.get(this.apiURLSeries, {
        params: this.apiParamsSeries
      })

      .then(res => {
        // console.log(res.data);
        this.seriesList = res.data.results;
      })

      .catch(err => {
        console.log(err);
      })
    },

    textToSearch(search) {
      this.apiParamsMovie.query = search;
      this.getApiMovie();
      this.apiParamsSeries.query = search;
      this.getApiSeries();
      console.log(search);
    },


  },

}


</script>

<style lang="scss">

  @import './assets/style/general';
  @import './assets/style/vars';
  @import './assets/style/mixins';

  .loader {
  position: relative;
  width: 100px;
  height: 100px;
  }

  .loader:before , .loader:after{
    content: '';
    border-radius: 50%;
    position: absolute;
    inset: 0;
    box-shadow: 0 0 10px 2px rgba(0, 0, 0, 0.3) inset;
  }

  .loader:after {
    box-shadow: 0 2px 0 #FF1111 inset;
    animation: rotate 2s linear infinite;
  }

  @keyframes rotate {
    0% {  transform: rotate(0)}
    100% { transform: rotate(360deg)}
  }
    

</style>
