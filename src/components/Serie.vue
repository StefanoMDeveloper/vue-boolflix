<template>
  <div>
    <li>
      <p>{{ info.name }}</p>
      <p>{{ info.original_name }}</p>
      <p><img :src="require(`../assets/img/${getFlags(info.original_language)}.png`)" :alt="info.original_language"></p>
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