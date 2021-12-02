<template>
  <section class="series">
    <h2 class="text-uppercase">Series</h2>
    <div class="container">
      <div class="row titles_container">
        <div 
          class="col-sm-4 col-md-3 col-xl-2 movie-cards"
          v-for="show in tvshow"
          :key="show.id"
        >
          <ul>
            <li>{{show.name}}</li>
            <li>{{show.original_name}}</li>
            <li>{{show.original_language}}</li>
            <li>{{show.vote_average}}</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Series',
  props:{
    tvshow: Array
  }
}
</script>

<style lang="scss">
@import '../assets/style/vars.scss';
@import '../assets/style/mixins.scss';

.series{
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