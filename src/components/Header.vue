<template>
  <header>
    <div class="container lv_container">
      <div class="logo text-uppercase">
        <img :src="require(`../assets/img/boolflix-logo.png`)" alt="">
      </div>
      <div class="search">
        <div class="input-group mb-3">
          <input 
            type="text" 
            class="form-control" 
            placeholder="Search..."
            v-model="titleToSearch"
            @keyup.enter="$emit('search', titleToSearch)"
          >
          <button 
            class="btn btn-outline-danger" 
            type="button"
            @click="$emit('search', titleToSearch)"
          >Search</button>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data(){
    return {
      titleToSearch: '',
    }
  }
}
</script>

<style lang="scss">
@import '../assets/style/vars.scss';
@import '../assets/style/mixins.scss';

header{
  background: linear-gradient(#000, rgba(0, 0, 0, 0.763));
  color: $primary-color;
  .lv_container{
    @include align();
    justify-content: space-between;
    height: 100px;
    .logo{
      width: 200px;
    }
    .logo img{
      max-width: 100%;
    }
  }
}


</style>