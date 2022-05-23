<template>
  
  <div class="card-series">
    <div class="flip-card">
      <div class="flip-card-inner">

        <div class="flip-card-front">
          <img v-if="series.poster_path" class="poster" :src="`https://image.tmdb.org/t/p/w342${series.poster_path}`" alt="Poster Movie">
          <img v-else class="poster" src="../assets/img/noposter.png" alt="No Poster Movie">
        </div>

        <div class="flip-card-back">
          <ul>
            <li>

              <h4>Titolo: {{series.name}}</h4>
              <h6>Titolo Originale: {{series.original_name}}</h6>

              <div v-if="series.original_language == 'en'"><span>Lingua Originale: </span><img src="../assets/img/eng.png" alt=""></div>

              <div v-else-if="series.original_language == 'it'"><span>Lingua Originale: </span><img src="../assets/img/ita.svg" alt=""></div>

              <div v-else-if="series.original_language == 'ja'"><span>Lingua Originale: </span><img src="../assets/img/jap.png" alt=""></div>

              <p v-else>Lingua Originale: {{series.original_language}}</p>
              <p>Voto: {{series.vote_average}}</p>
              <p>Sinossi: </p>
              <p>{{series.overview}}</p>

            </li>
          </ul>
        </div>

      </div>
    </div>
  </div>

</template>

<script>

export default {
  name: 'SeriesComponent',

  props: {
    series: Object
  }

}
</script>

<style lang="scss" scoped>

  ul {
    list-style: none;
    padding: 0 10px;
    text-align: center;
  }

  img {
    width: 35px;
  }

  .poster {
    width: 250px;
    height: 350px;
  }

  .card-series {
    width: 250px;
    height: 350px;
    margin: 30px 10px;
    color: #FFFFFF;
  }

  .flip-card {
    background-color: transparent;
    width: 250px;
    height: 350px;
    perspective: 1000px;
    
  }

  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.8s;
    transform-style: preserve-3d;
    
  }

  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
  }

  .flip-card-front, .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
  }

  .flip-card-back {
    background-color: #252525;
    color: white;
    transform: rotateY(180deg);
    overflow-y: auto;
  }

</style>