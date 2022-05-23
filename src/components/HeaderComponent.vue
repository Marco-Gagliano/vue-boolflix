<template>
  
  <header class="container-fluid">

    <div class="container d-flex justify-content-between align-items-center">

      <img src="https://www.romait.it/wp-content/uploads/2022/04/Netflix-logo.jpg" alt="Netflix Logo">

      <div class="search-movies">

        <input  @keyup.enter="$emit('startSearch', searchTitle)"
                v-model="searchTitle"
                class="form-control"
                type="text" 
                placeholder="Esegui qui la tua ricerca... ">

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

  methods:{
    startSearch() {
      this.$emit('startSearch', this.searchTitle);
      this.searchTitle = '';
    }
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
    text-align: center;
    border-radius: 5px;
    border: 0px;
  }

  
  img {
    width: 22%;
  }


</style>