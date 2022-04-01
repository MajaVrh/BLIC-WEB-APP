<template>
  <div class="parent">
    <button @click="vratiSe">Home</button>
    <br />
    <div class="knjigaaa">
      <div>ISBN: {{ knjiga.isbn }}</div>
      <div>BROJ STRANICA: {{ knjiga.numberOfPages }}</div>
      <div>IZDAVAČ: {{ knjiga.publisher }}</div>
      <div>AUTORI: {{ knjiga.authors }}</div>
      <div>DRŽAVA: {{ knjiga.country }}</div>
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
      knjiga: [],
    };
  },
  async mounted() {
    await this.fetchKnjiga();
  },
  methods: {
    async fetchKnjiga() {
      const id = this.$route.params.id;
      console.log("ID U RUTERU, id");
      const pomocni = await axios.get(id);

      console.log(id);
      this.knjiga = pomocni.data;
    },
    vratiSe() {
      this.$router.push({ name: "Home" });
    },
  },
};
</script>
<style scoped>
.knjigaaa {
  background-color: yellow;
  padding: 3rem;
  width: 30%;
  border-radius: 10%;
}
.parent {
  display: flex;
  justify-content: center;
  align-items: center;
}
button {
  padding: 1rem;
  border-radius: 10px;
  margin-right: 5rem;
}
</style>
