<template>
  <div>
    <li>
      <p>
        <img
          :src="`https://image.tmdb.org/t/p/w185${info.poster_path}`"
          alt=""
        />
      </p>
      <p>{{ info.name }}</p>
      <p>{{ info.original_name }}</p>
      <p>
        <img :src="require(`../assets/img/${getFlags(info.original_language)}.png`)" :alt="info.original_language"
        />
      </p>
      <span v-for="(element, i) in stelle" :key="i">
        <i class="fa-solid fa-star"></i>
      </span>
      <p>{{ info.vote_average }}</p>
    </li>
  </div>
</template>

<script>
export default {
  name: "Serie",
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
      parseInt(voto);
      let arrayStelle = [];
      for (let i = 0; i < (voto/2); i++) {
        arrayStelle.push(i);
      }
      return arrayStelle;
    },
  },
};
</script>

<style>
</style>