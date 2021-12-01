<template>
  <header>
    <div class="container lv_container">
      <div class="logo text-uppercase">
        <h1>Boolflix</h1>
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
  background-color: #000;
  color: $primary-color;
  .lv_container{
  @include align();
  justify-content: space-between;
  height: 100px;
  }
}


</style>