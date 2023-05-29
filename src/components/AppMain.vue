<script >
import { store } from '../data/store';

export default {
  name: "ma",
  data() {
    return {
      store

    }
  },
  methods: {
    printData() {

    }
  }
}    
</script>

<template>
  <div class="logo">
    <img src="../assets/Screenshot 2023-05-29 015107.png" alt="">
    <h1>Yu-Gi-Oh Api</h1>
  </div>
  <div class="container">

    <div class="cards">
      <div class="titoloCards">Found 40 cards</div>
      <div v-for="c, i in store.carte " class="card">
        <img :src="store.carte[i].card_images[0].image_url" alt="">
        <span>{{ store.carte[i].name }}</span>
        <div>{{ store.carte[i].archetype }}</div>
      </div>
    </div>

  </div>
</template>

<style lang="scss" scoped>
@use '../styles/_variables' as *;

.logo {
  width: 100vw;
  height: 5.36rem;
  background-color: #ffffff;
  padding-left: 1rem;
  display: flex;
  align-items: center;
  gap: 2rem;

  img {
    height: 5rem;
  }
}

.container {
  width: 100vw;
  min-height: calc(100vh - 5.36rem);
  background-color: #d48f38;
  display: flex;
  justify-content: center;
  align-items: center;

}

.cards {
  width: 90%;
  min-height: 90%;
  background-color: #ffffff;
  padding: 2rem;
  display: flex;
  flex-wrap: wrap;
  gap: 0.9rem;
}

.titoloCards {
  width: 100vw;
  background-color: #212529;
  color: white;
  height: 2.5rem;
  padding-left: 1rem;
  display: flex;
  align-items: center;
}

.card {
  width: 14.3rem;
  height: 26rem;
  background-color: #d48f38;
  display: flex;
  flex-direction: column;
  align-items: center;


  img {
    width: 100%;
    margin-bottom: 1rem
  }

  ;

  span {
    color: white;
    margin-bottom: 1rem
  }
}
</style>
