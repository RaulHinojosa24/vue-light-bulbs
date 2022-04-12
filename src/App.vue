<script setup>
import LightBulb from './components/LightBulb.vue';
import logo from './assets/logo.svg'
</script>

<script>
  export default {
    data() {
      return {
        clickRange: 5,
        totalBulbs: 5,
        bulbsSwitchedOn: 0,
        allOn: false
      }
    },
    methods: {
      onBulbSwitchedOn() {
        console.log("ensendida")
        this.bulbsSwitchedOn++;

        if (this.bulbsSwitchedOn == this.totalBulbs) {
          this.allOn = true;
        }
      },
      getRandomClickRange() {
        return Math.floor(Math.random() * this.clickRange) + 1;
      }
    }
  }
</script>

<template>
  <main>
    <img :src="logo" alt="Logo" id="logo">

    <div>
      <h1 v-if="allOn">Todas las bombillas están encendidas!</h1>
      <h1 v-else>Faltan bombillas por encender!</h1>
    </div>
    <div class="bulbs">
      <LightBulb v-for="n in totalBulbs" :key="n" :neededClicks="getRandomClickRange()" @switchedOn="onBulbSwitchedOn"/>
    </div>
  </main>
</template>

<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

#logo {
  width: 200px;
}

main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.bulbs {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
}

h1{
  text-align: center;
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }
}
</style>
