<script >
import { store } from '../data/store';
import axios from 'axios';


export default {
  name: "AppMain",
  components: {

  },
  data() {
    return {
      store,
      opzioniSelezionabili: [
        "Alien",
        "ABC",
        "@Ignister"
      ],
      archetypeScelto: "Alien"


    }
  },
  methods: {
    printCarte() {
      let indirizzo = "https://db.ygoprodeck.com/api/v7/cardinfo.php"
      if (this.archetypeScelto == "Alien") {
        indirizzo += "?archetype=Alien"
      } else if (this.archetypeScelto == "ABC") {
        indirizzo += "?archetype=ABC"
      } else {
        indirizzo += "?archetype=@Ignister"
      };
      axios.get(indirizzo).then(result => {
        const risulataato = result.data;
        this.store.carte = risulataato.data;
      }).catch(err => {
        this.store.carte = {};
      });

    }
  },
  computed: {
    filtraCarte() {
      return this.store.carte.slice(0, 40)
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

    <select @click="printCarte" v-model="archetypeScelto" class="selezionaCarte">
      <option v-for="opzione in opzioniSelezionabili">{{ opzione }}</option>
    </select>

    <div class="cards">
      <div class="titoloCards">Found 40 cards</div>
      <div v-for="c, i in filtraCarte" class="card">
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
  position: relative;

}

.selezionaCarte {
  width: 8rem;
  border-radius: 5px;
  padding: 0.3rem;
  border: none;
  position: absolute;
  top: 0.7rem;
  left: 8rem;
}

.cards {
  width: 85%;
  min-height: 90%;
  background-color: #ffffff;
  padding: 2rem 4rem;
  margin: 3rem;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 2rem;
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
