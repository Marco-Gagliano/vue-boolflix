<template>

  <div class="card-movie">

    <ul>
      <li>
        <h4>Titolo: {{movie.title}}</h4>
        <h6>Titolo Originale: {{movie.original_title}}</h6>
        <div v-if="movie.original_language == 'en'"><span>Lingua Originale: </span><img src="../assets/img/eng.png" alt=""></div>
        <div v-else-if="movie.original_language == 'it'"><span>Lingua Originale: </span><img src="../assets/img/ita.svg" alt=""></div>
        <div v-else-if="movie.original_language == 'ja'"><span>Lingua Originale: </span><img src="../assets/img/jap.png" alt=""></div>
        <p v-else>Lingua Originale: {{movie.original_language}}</p>
        <p>Voto: {{movie.vote_average}}</p>
        <p>Sinossi: </p>
        <p>{{movie.overview}}</p>
      </li>
    </ul>

  </div>

</template>

<script>

export default {
  name: "MovieComponent",
  
  props: {
    movie: Object
  }

}
</script>

<style lang="scss" scoped>

  ul {
    list-style: none;
  }

  img {
    width: 35px;
  }

  .card-movie {
    width: 250px;
    height: 350px;
    background-color: #252525;
    border: 1px solid #FF1111;
    margin: 30px 10px;
    color: #FFFFFF;
    overflow-y: auto;
  }

</style>