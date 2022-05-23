<template>

  <div class="card" >

    <div v-for="card in movieList" :key="`movie${card.id}`" :dataCard="card"> 
      <h3>Titolo{{card.title}}</h3>
      <p>Titolo originale{{card.original_title}}</p>
      <p>Lingua{{card.original_language}}</p>
      <p>Voto{{card.vote_average}}</p>
    </div>
      

  </div>

</template>

<script>
export default {
  name: 'CardComponent',

  props: {
    dataCard: Object
  }
}
</script>

<style lang="scss" scoped>

  .card {
    width: 200px;
    height: 350px;
    background-color: #252525;
    border: 1px solid #FF1111;
    margin: 30px 25px;
    text-align: center;
    color: #FFFFFF;
    
  }

</style>