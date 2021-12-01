<template>
  <div id="app">
    <Header
    @search='searchTitle'
    />
    <Main/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from "axios";

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return {
      titles: [],
      query: '',
      api_url: 'https://api.themoviedb.org/3/search/movie',
      api_key: '3ba064683997e5f14efec0c929a4546e',
    }
  },
  methods: {
    searchTitle(data){
      //console.log({data});
      this.query = data;
      axios.get(this.api_url,{
        params: {
          api_key: this.api_key,
          query: this.query
        }
      })
        .then(response => {
          console.log(response);
          this.titles = response.data.results;
        })
        .catch(error => {
          console.log(error);
        })
    }
  },
}
</script>

<style lang="scss">
@import './assets/style/vars.scss';
@import './assets/style/generals.scss';
@import './assets/style/mixins.scss';
#app{
  min-height: 100vh;
}
</style>
