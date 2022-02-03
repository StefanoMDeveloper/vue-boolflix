<template>
  <div>
    <li>
      <p>{{ info.title }}</p>
      <p>{{ info.original_title }}</p>
      <p>{{ info.original_language }}</p>
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
  methods: {},
};
</script>

<style>
</style>