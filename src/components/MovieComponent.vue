<template>

  <div class="card-movie">
  <CardComponent  v-for="(movie, index) in listMovie"
                    :key="`album${index}`"
                    :title="movie.title"
                    :originalTitle="movie.original_title"
                    :language="movie.language"
                    :vote="movie.vote"
                    />
  </div>

</template>

<script>

import CardComponent from './CardComponent.vue';

export default {
    name: "MovieComponent",
    components: { CardComponent },
    props: {
      listMovie: Array
    }


}
</script>

<style lang="scss" scoped>

.card-movie {
    width: 200px;
    height: 350px;
    background-color: #252525;
    border: 1px solid #FF1111;
    margin: 30px 25px;
    text-align: center;
    color: #FFFFFF;
    
  }

</style>