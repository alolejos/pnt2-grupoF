<script setup>
import Header from './components/Header.vue'
import Instrumentos from './components/Instrumentos.vue'
import AgregarInstrumento from './components/AgregarInstrumento.vue'
</script>

<template>
  <header>
    <!--<img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
    -->
    <Header/> 
  </header>

  <main>
    <TheWelcome />
    <Instrumentos v-bind:instrumento="instrumento" @borrarInstrumento="borrarInstrumento"/>
    <AgregarInstrumento v-bind:instrumento="instrumento" @agregarInst="agregarInstrumento" />
  </main>
</template>

<script>
export default {
  data() {
    return {
      instrumento: [
        {id: 1, tipo: "Guitarra", modelo: "Gibson"},
        {id: 2, tipo: "Piano", modelo: "Digital"},
        {id: 3, tipo: "Violin", modelo: "Cuerdas"},
        {id: 4, tipo: "Piano", modelo: "Cola"}
      ]
    }
  },
  methods: {
    agregarInstrumento(newInst) {
      this.instrumento.push(newInst);
    },
    borrarInstrumento(i) {
      this.instrumento.splice(i, 1);
    }
    
  }
};
</script>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
