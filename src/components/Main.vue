<template>
  <main>
    <div class="container">
      <Movies :movies="moviesList" />
      <Series :tvshow="tvshowList" />
    </div>
  </main>
</template>

<script>
import Movies from "./Movies.vue";
import Series from "./Series.vue";

export default {
  name: "Main",
  components: {
    Movies,
    Series,
  },
  props: {
    moviesList: Array,
    tvshowList: Array,
  },
};
</script>

<style lang="scss">
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";
main {
  background-color: #434343;
  min-height: calc(100vh - 100px);
}
</style>
