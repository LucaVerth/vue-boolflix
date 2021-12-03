<template>
  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img
          v-if="sendTitle.poster_path"
          :src="`https://image.tmdb.org/t/p/w342${sendTitle.poster_path}`"
          alt=""
        />
        <p class="d-flex flex-column bg-light" v-else>
          <span class="">{{ sendTitle.name }}</span>
          <span class="py-3">PLACEHOLDER IMG</span>
        </p>
      </div>
      <div class="flip-card-back">
        <ul class="d-flex flex-column align-items-baseline">
          <li>{{ sendTitle.name }}</li>
          <li>{{ sendTitle.original_name }}</li>
          <li>
            <strong>Lingua:</strong>
            <img
              class="lang-flag"
              :src="require(`../assets/img/${sendTitle.original_language}.png`)"
              :alt="sendTitle.original_language"
            />
          </li>
          <li>
            <strong>Voto: </strong>
            <i
              v-for="(star, index) in 5"
              :key="index"
              class="fa-star"
              :class="
                index < Math.round(sendTitle.vote_average / 2) ? 'fas' : 'far'"></i></li>
          <li><strong>Overview: </strong>{{ sendTitle.overview }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Seriescard",
  props: {
    sendTitle: Object,
  },
  data() {
    return {
      langFlag: ["it", "en"],
    };
  },
};
</script>

<style lang="scss">
@import "~@fortawesome/fontawesome-free/css/all.min.css";

.flip-card {
  background-color: transparent;
  height: 450px;
  perspective: 1000px;
  cursor: pointer;
}
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}
.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}
.flip-card-front {
  background-color: transparent;
  color: black;
}
.flip-card-front img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.flip-card-back {
  background-color: #000;
  color: white;
  transform: rotateY(180deg);
  overflow: auto;
  ul {
    list-style-type: none;
    margin: 20px 0;
    padding: 0 10px;
    li {
      text-align: left;
    }
  }
}
.lang-flag {
  width: 25px;
  margin: 10px;
}
.placeholder {
  background-color: #fff;
}
</style>
