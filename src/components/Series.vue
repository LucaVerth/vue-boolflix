<template>
  <section class="series">
    <h2 class="text-uppercase">Series</h2>
    <div class="container">
      <div class="row titles_container">
        <div
          class="col-sm-6 col-md-4 col-xl-3 series-cards"
          v-for="show in tvshow"
          :key="show.id"
        >
          <Seriescard :sendTitle="show" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Seriescard from "./Seriescard.vue";

export default {
  name: "Series",
  components: {
    Seriescard,
  },
  props: {
    tvshow: Array,
  },
};
</script>

<style lang="scss">
@import "../assets/style/vars.scss";
@import "../assets/style/mixins.scss";

.series {
  h2 {
    color: $primary-color;
    text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
  }
  .series-cards {
    margin: 10px;
  }
  .titles_container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
  }
}
</style>
