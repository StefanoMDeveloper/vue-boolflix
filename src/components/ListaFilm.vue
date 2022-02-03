<template>
  <div>
    <Cerca @filtra="filtraFilm"/>
    <ul>
      <Film v-for="(elem, index) in filmFiltrati" :key="index" :info="elem"/>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import Cerca from "./Cerca.vue";
import Film from "./Film.vue";
export default {
  name: "ListaFilm",
  components: {
    Cerca,
    Film,
  },
  data() {
    return {
      arrayFilm: [],
      valueInput: "one piece",
    };
  },
  computed: {
    filmFiltrati() {
      return this.arrayFilm.filter((film) => {
        console.log(this.valueInput);
        return film.title.toLowerCase().includes(this.valueInput.toLowerCase());
      });
    },
  },
  created() {
    this.getFilm();
  },
  methods: {
    filtraFilm (inputRicevuto) {
      this.valueInput = inputRicevuto;
      this.getFilm();
    },
    getFilm () {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "3357ea4f20256909db5e4b32656fede0",
            query: this.valueInput,
          },
        })
        .then((response) => {
          console.log(response.data);
          this.arrayFilm = response.data.results;
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>

<style scoped lang="scss">
</style>