<template>
  <div>
      <ListaFilm />
  </div>
</template>

<script>

import ListaFilm from "./ListaFilm.vue"
export default {
    name: "Main",
    components: {
        ListaFilm
    }
}
</script>

<style scoped lang="scss">
    div{
        background-color: rgb(67, 67, 67);
    }
</style>