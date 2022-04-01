<template>
  <div>
    <div class="knjiga" v-for="k of knjiga" :key="k.url">
      <div>aa{{ k.isbn }}</div>
      <div>{{ k.numberOfPages }}</div>
      <div>{{ k.isbn }}</div>
      <div>{{ k.authors }}</div>
      <div>{{ k.country }}</div>
      <!--   <div>{{ k.characters }}</div>-->
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "knjiga",
  data() {
    return {
      knjiga: {},
    };
  },
  methods: {
    async fetchKnjiga() {
      const id = this.$route.params.idRoutera;
      const pomocni = await axios.get(
        `https://www.anapioficeandfire.com/api/books/${id}`
      );
      this.knjiga = pomocni.data;
    },
  },
};
</script>
