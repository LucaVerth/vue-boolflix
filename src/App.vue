<template>
  <div id="app">
    <Header @search="searchTitle" />
    <Main 
      :moviesList="titlesMovies"
      :tvshowList="titlesTv"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      titlesMovies: [],
      titlesTv: [],
      api_url_movie: "https://api.themoviedb.org/3/search/movie",
      api_url_tvshow: "https://api.themoviedb.org/3/search/tv",
      params: {
        api_key: "3ba064683997e5f14efec0c929a4546e",
        query: "",
      },
    };
  },
  methods: {
    // double axios call for both movies and tv series
    searchTitle(data) {
      //console.log({data});
      this.params.query = data;

      const movieRequest = axios.get(this.api_url_movie, {
        params: this.params,
      });
      const tvShowRequest = axios.get(this.api_url_tvshow, {
        params: this.params,
      });

      axios
        .all([movieRequest, tvShowRequest])
        .then(
          axios.spread((...result) => {
            this.titlesMovies = result[0].data.results;
            this.titlesTv = result[1].data.results;

            console.log(this.titlesMovies);
            console.log(this.titlesTv);
          })
        )
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/generals.scss";
@import "./assets/style/mixins.scss";
#app {
  min-height: 100vh;
}
</style>
