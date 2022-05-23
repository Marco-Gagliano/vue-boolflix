<template>

  <div>
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

</style>