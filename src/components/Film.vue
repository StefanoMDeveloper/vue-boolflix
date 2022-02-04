<template>
  <div>
    <li>
      <p><img :src="`https://image.tmdb.org/t/p/w185${info.poster_path}`" alt=""></p>
      <p>{{ info.title }}</p>
      <p>{{ info.original_title }}</p>
      <p><img :src="require(`../assets/img/${getFlags(info.original_language)}.png`)" :alt="info.original_language"></p>
      <p>{{ info.vote_average }}</p>
    </li>
  </div>
</template>

<script>
export default {
  name: "Film",
  props: {
    info: Object,
  },
  methods: {
    getFlags: function(language){
      let urlFlag = "jolly";
      if(['it', 'en'].includes(language)){
        urlFlag = language;
      }
      return urlFlag;
    }
  },
};
</script>

<style>
</style>