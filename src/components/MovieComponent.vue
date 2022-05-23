<template>

  <div class="card-movie">

  <ul>
    <li>
      <h4>Titolo: {{movie.title}}</h4>
      <h6>Titolo Originale: {{movie.original_title}}</h6>
      <p>Lingua Originale: {{movie.original_language}}</p>
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