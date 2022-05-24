<template>
  
  <header class="container-fluid">
    <div class="container d-flex justify-content-between  align-items-center">

      <img src="https://www.romait.it/wp-content/uploads/2022/04/Netflix-logo.jpg" alt="Netflix Logo">

      <div class="search-movies d-flex">

        <input  @keyup.enter="startSearch()"
                v-model.trim="searchTitle"
                class="form-control"
                type="text" 
                placeholder="Esegui qui la tua ricerca... ">
        
      <button @click="startSearch()">RICERCA</button>

      </div>


    </div>
  </header>
  
</template>


<script>
export default {

  name: 'HeaderComponent',

  data(){
    return {
      searchTitle: ''
    }
  },

  methods: {
    startSearch(){
      this.$emit( 'startSearch', this.searchTitle );
      this.searchTitle= '';
    },
  }
}

</script>


<style lang="scss" scoped>

  header {
    background-color: #000000;
    border-bottom: 1px solid #FF1111;
  }

  input {
    margin: 0 20px;
    padding: 5px 15px;
    border: 0px;
    background-color: #000000;
    border: 2px solid #FFFFFF;
    color: #FFFFFF;
  }

  input:focus {
    background-color: #000000;
    color: #FFFFFF;
  }

  input::placeholder {
    color: #FFFFFF
  }


  button {
    background-color: #000000;
    color: #FF1111;
    border: 2px solid #FF1111;
  }

  button:hover {
    background-color: #FF1111;
    color: #000000;
    border: 2px solid #FF1111;
  }

  img {
    width: 22%;
  }

</style>