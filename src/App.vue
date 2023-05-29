<script >
import AppMain from './components/AppMain.vue';

import { store } from './data/store';
import axios from 'axios';

export default {
  nome: "app",
  components: {
    AppMain
  },
  data() {
    return {
      store
    }
  },
  mounted() {

    axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php").then(result => {
      const risulataato = result.data;
      console.log("chiama");
      this.store.carte = risulataato.data;
    });
  }

}

</script>

<template>
  <AppMain />
</template>

<style lang="scss" scoped></style>
