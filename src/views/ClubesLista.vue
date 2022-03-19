<template>
  <v-container>
    <h2 class="text-h5 text-center mb-3 mt-5">Classificação dos clubes</h2>
    <ClubesTabelas :clubes="ordenarClubes"/>
  </v-container>
</template>


<script>
import ClubesTabelas from "../components/shared/ClubesTabelas.vue";

export default {
  name: "ClubesLista",
  data(){
      return{
          listaClubes: []
      }
  },
  components: {
    ClubesTabelas,
  },
  created() {
    fetch("https://hackthon-decola.firebaseio.com/clubes-lista.json", {
      method: "GET",
    }).then((res) => {
      res.json().then((result) => {
        this.listaClubes = result;
      });
    });
  },
  computed: {
    ordenarClubes() {
      const clubesOrdenados = this.listaClubes.slice(0).sort((a, b) => {
        return a.pontos > b.pontos ? -1 : 1
      });
      return clubesOrdenados;
    }
  }
};
</script>

<style scoped>
</style>