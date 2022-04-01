<template>
  <div>
    <div
      class="card"
      v-for="knjiga in knjige"
      :key="knjiga.isbn"
      @click="odvediMe(knjiga.isbn)"
    >
      <div>{{ knjiga.name }}</div>
      <div>{{ knjiga.authors }}</div>
      <div>{{ knjiga.released }}</div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import axios from "axios";
export default {
  name: "Home",

  data() {
    return {
      knjige: [],
    };
  },

  components: {
    HelloWorld,
  },
  async mounted() {
    await this.fetchKnjige();
  },
  methods: {
    async fetchKnjige() {
      const pomocni = await axios.get(
        "https://www.anapioficeandfire.com/api/books"
      );
      const data = pomocni.data;
      console.log(data);
      this.knjige = data;
    },
    odvediMe(id) {
      this.$router.push({ name: "knjiga", parms: { idRoutera: id } });
    },
  },
};
</script>

<style scoped>
.card {
  background-color: yellow;
  margin: 3rem;
}
</style>
