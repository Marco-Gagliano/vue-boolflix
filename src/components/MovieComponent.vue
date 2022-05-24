<template>

  <div class="card-movie">
    <div class="flip-card">
      <div class="flip-card-inner">

        <div class="flip-card-front">
          <img v-if="movie.poster_path" class="poster" :src="`https://image.tmdb.org/t/p/w342${movie.poster_path}`" alt="Poster Movie">
          <img v-else class="poster" src="../assets/img/noposter.png" alt="No Poster Movie">
        </div>

        <div class="flip-card-back">
          <ul>
            <li>

              <h4>Titolo: {{movie.title}}</h4>
              <h6>Titolo Originale: {{movie.original_title}}</h6>

              <div v-if="movie.original_language == 'en'"><span>Lingua Originale: </span><img src="../assets/img/eng.png" alt=""></div>

              <div v-else-if="movie.original_language == 'it'"><span>Lingua Originale: </span><img src="../assets/img/ita.svg" alt=""></div>

              <div v-else-if="movie.original_language == 'ja'"><span>Lingua Originale: </span><img src="../assets/img/jap.png" alt=""></div>

              <p v-else>Lingua Originale: {{movie.original_language}}</p>
              
              <p>Voto:

                <span v-for="(star, i) in voteStars()" :key="`star${i}`">
                  <i class="fa-solid fa-star"></i>
                </span>

                <span v-for="(emptyStar, i) in emptyStars()" :key="`emptyStar${i}`">
                  <i class="fa-regular fa-star"></i>
                </span>

                {{movie.vote_average / 2}}
              
              </p>

              <p>Sinossi: </p>
              <p>{{movie.overview}}</p>

            </li>
          </ul>
        </div>

      </div>
    </div>
  </div>

</template>


<script>

export default {
  name: "MovieComponent",
  
  props: {
    movie: Object,
  },

  data(){
    return {
      maxStars: 5
    };
  },

  methods: {
    voteStars() {
      return Math.round(this.movie.vote_average / 2);
    },

    emptyStars() {
      return this.maxStars - this.voteStars();
    },
  },

}
</script>


<style lang="scss" scoped>

  @import '../assets/style/vars';

  ul {
    list-style: none;
    padding: 0 10px;
    text-align: center;
  }

  img {
    width: 35px;
  }

  .poster {
    width: 400px;
    height: 550px;
  }

  .card-movie {
    width: 400px;
    height: 600px;
    margin: 20px 5px;
    color: #FFFFFF;
  }

  .flip-card {
    background-color: transparent;
    width: 400px;
    height: 550px;
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