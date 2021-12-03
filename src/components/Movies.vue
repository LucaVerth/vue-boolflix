<template>
  <section class="movies">
    <h2 class="text-uppercase">Movies</h2>
    <div class="container">
      <div 
        class="row titles_container"
      >
        <div
          class="col-sm-12 col-md-4 col-xl-3 movie-cards"
          v-for="movie in movies"
          :key="movie.id"
        >
          <Moviecard :sendTitle="movie" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Moviecard from "./Moviecard.vue";

export default {
  name: "Movies",
  components: {
    Moviecard,
  },
  props: {
    movies: Array,
  },
};
</script>

<style lang="scss">
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";

.movies {
  h2 {
    color: $primary-color;
    text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
  }
  .movie-cards {
    margin: 10px;
  }
  .titles_container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
  }
}
</style>
