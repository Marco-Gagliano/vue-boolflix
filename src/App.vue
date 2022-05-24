<template>

  <div id="app">

    <div v-if="loadingPage">
    
      <HeaderComponent @startSearch="textToSearch"/>
      <MainComponent itemTitle="Film" :movieList="movieList"/>
      <MainComponent itemTitle="Serie TV" :seriesList="seriesList"/>

    </div>

    <div v-else class="screen"></div>
  
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
      apiURLSeries: "https://api.themoviedb.org/3/search/tv",
      apiParams: {
        api_key: "6bb3bf68889e21ad45904086318351a4",
        language: "it-IT",
        query: "",
      },
      movieList: [],
      seriesList: [],
      loadingPage: false,
    }
  },

  methods: {

    getApiMovie(){
      axios.get(this.apiURLMovie, {
        params: this.apiParams
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
        params: this.apiParams
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
      this.apiParams.query = search;
      this.getApiMovie();
      this.getApiSeries();
      // console.log(search);
    },

    screenSite() {
      this.loadingPage = true
    }
  },

  mounted() {
    setTimeout(this.screenSite, 3500)
  }
}

</script>


<style lang="scss">

  @import './assets/style/general';
  @import './assets/style/vars';
  @import './assets/style/mixins';

  .screen {
    background-image: url(./assets/img/2772922.webp);
    background-size: cover;
    background-position: center;
    // width: 100vw;
    height: 100vh;
  }

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
