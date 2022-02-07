<template>
  <div class="cards col">
    <div class="poster">
      <img :src="`https://image.tmdb.org/t/p/w300${info.poster_path}`" alt="" />
    </div>

    <div class="cards-text-container">
      <p>{{ info.title }}</p>
      <p>{{ info.original_title }}</p>
      <p>
        <img
          :src="
            require(`../assets/img/${getFlags(info.original_language)}.png`)
          "
          :alt="info.original_language"
        />
      </p>
      <span v-for="(element, i) in stelle" :key="i">
        <i class="fas fa-solid fa-star"></i>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Film",
  props: {
    info: Object,
  },
  data() {
    return {
      stelle: this.getNStars(this.info.vote_average),
    };
  },
  methods: {
    getFlags: function (language) {
      let urlFlag = "jolly";
      if (["it", "en"].includes(language)) {
        urlFlag = language;
      }
      return urlFlag;
    },
    getNStars: function (voto) {
      voto = Math.ceil(voto);
      let arrayStelle = [];
      for (let i = 0; i < voto / 2; i++) {
        arrayStelle.push(i);
      }
      return arrayStelle;
    },
  },
};
</script>

<style scoped lang="scss">
.cards {
  height: 450px;
  width: 300px;
  position: relative;
  background-color: black;
  color: white;


  .poster {
    position: absolute;
    top: 0;
    left: 0;
      z-index: 1;
    &:hover {
      display: none;
    }
    img {
      height: 450px;
      width: 300px;
    }
  }
}

.cards-text-container {
  position: absolute;
  z-index: 0;
  top: 0;
  right: 0;
  height: 450px;
  width: 300px;
  padding: 10px;
}

.fa-star {
  color: orange;
}
</style>