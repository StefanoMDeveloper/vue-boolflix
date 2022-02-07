<template>
  <div class="container p-4">
    <Cerca @filtra="filtraRicerca" />
    <h1>Film</h1>
    <div class="card-container row row-cols-4 pe-0 g-1">
      <Film v-for="(elem, index) in filmFiltrati" :key="index" :info="elem" class="col"/>
    </div>
    <h1>Serie TV</h1>
    <div class="card-container row row-cols-4 pe-0 g-1">
      <Serie v-for="(elem, index) in serieFiltrate" :key="index" :info="elem" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Cerca from "./Cerca.vue";
import Film from "./Film.vue";
import Serie from "./Serie.vue";
export default {
  name: "ListaFilm",
  components: {
    Cerca,
    Film,
    Serie,
  },
  data() {
    return {
      arrayFilm: [],
      arraySerie: [],
      valueInput: "harry potter",
    };
  },
  computed: {
    filmFiltrati() {
      return this.arrayFilm.filter((film) => {
        console.log(this.valueInput);
        return film.title.toLowerCase().includes(this.valueInput.toLowerCase());
      });
    },
    serieFiltrate() {
      return this.arraySerie.filter((serie) => {
        console.log(this.valueInput);
        return serie.name.toLowerCase().includes(this.valueInput.toLowerCase());
      });
    },
  },
  created() {
    this.getFilm();
    this.getSerie();
  },
  methods: {
    filtraRicerca(inputRicevuto) {
      this.valueInput = inputRicevuto;
      this.getFilm();
      this.getSerie();
    },
    getFilm() {
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
    getSerie() {
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "3357ea4f20256909db5e4b32656fede0",
            query: this.valueInput,
          },
        })
        .then((response) => {
          console.log(response.data);
          this.arraySerie = response.data.results;
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>

<style scoped lang="scss">
  h1{
    color: black;
    margin-top: 20px;
  }
</style>