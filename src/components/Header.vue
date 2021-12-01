<template>
  <header>
    <div class="container-fluid lv_container">
      <div class="logo text-uppercase">
        <h1>Boolflix</h1>
      </div>
      <div class="search">
        <div class="input-group mb-3">
          <input type="text" class="form-control" placeholder="Search...">
          <button class="btn btn-outline-danger" type="button">Search</button>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',

}
</script>

<style lang="scss">
@import '../assets/style/vars.scss';
@import '../assets/style/mixins.scss';

.lv_container{
  @include align();
  justify-content: space-between;
  height: 100px;
  background-color: #000;
  color: $primary-color;
}

</style>