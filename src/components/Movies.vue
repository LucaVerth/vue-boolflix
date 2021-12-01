<template>
  <section class="movies">
    <h2 class="text-uppercase">Movies</h2>
    <div class="container">
      <div class="row titles_container">
        <div 
          class="col-sm-4 col-md-3 col-xl-2 movie-cards"
          v-for="movie in movies"
          :key="movie.id"
        >
          <ul>
            <li>{{movie.title}}</li>
            <li>{{movie.original_title}}</li>
            <li>{{movie.original_language}}</li>
            <li>{{movie.vote_average}}</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Movies',
  props:{
    movies: Array
  }
}
</script>

<style lang="scss">
@import '../assets/style/vars.scss';
@import '../assets/style/mixins.scss';

.movies{
  h2{
    color: $primary-color;
  }
  .movie-cards{
    background-color: #fff;
    margin: 10px;
  }
  .titles_container{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
  }
}


</style>