<script >

export default {
  name: "AppPersonaggio",
  data() {
    return {
      store

    }
  },
  methods: {

  }
}     
</script>

<template>
  <img :src="store.carte[i].card_images[0].image_url" alt="">
  <span>{{ store.carte[i].name }}</span>
  <div>{{ store.carte[i].archetype }}</div>
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
