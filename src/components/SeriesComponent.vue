<template>
  
  <div class="card-series">

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
  }

  img {
  width: 35px;
  }

  .card-series {
    width: 250px;
    height: 350px;
    background-color: #252525;
    border: 1px solid #FF1111;
    margin: 30px 25px;
    color: #FFFFFF;
    overflow-y: auto;
  }

</style>