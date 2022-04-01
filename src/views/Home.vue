<template>
  <div class="parent">
    <div
      class="card"
      v-for="knjiga in knjige"
      :key="knjiga.url"
      @click="odvediMe(knjiga.url)"
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
      console.log("evo", data);
      this.knjige = data;
    },
    odvediMe(id) {
      console.log("ID:", id);
      this.$router.push({ name: "knjiga", params: { id: id } });
    },
  },
};
</script>

<style scoped>
.card {
  background-color: yellow;
  padding: 3rem;
  width: 50%;
  border-radius: 10%;
  margin: 2rem;
}

.parent {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
