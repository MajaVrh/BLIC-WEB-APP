<template>
  <div>
    <div class="knjiga" v-for="k in knjiga" :key="k.isbn"></div>
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
      const id = this.$route.params.id;
      const pomocni = await axios.get(
        `https://www.anapioficeandfire.com/api/books/${id}`
      );
      this.knjiga = pomocni.data;
    },
  },
};
</script>
