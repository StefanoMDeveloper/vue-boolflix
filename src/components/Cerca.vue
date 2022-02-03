<template>
  <div>
    <input type="text" v-model="inputText" placeholder="Cerca..."/>
    <button @click="inviaInput">Cerca</button>
  </div>
</template>

<script>

export default {
  name: "Cerca",
  data() {
    return {
        inputText: ""
    };
  },
  methods: {
      inviaInput: function(){
          this.$emit('filtra', this.inputText);
      }
  }
};
</script>

<style scoped lang="scss">
</style>