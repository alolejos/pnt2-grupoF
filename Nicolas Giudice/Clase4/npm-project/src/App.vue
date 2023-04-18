<script setup>
  import AddNewCar from "./components/AddNewCar.vue";
  import CarsList from "./components/CarsList.vue";
  import Header from "./components/Header.vue";
</script>

<template>
  <header>
    <Header />
  </header>

  <main>
    <CarsList :cars="cars" @deleteCarOfList="deleteCrr"/>
    <AddNewCar :lastIndex="lastIndex" @addCarInList="addCar"/>
  </main>
</template>

<script>
  export default {
    data() {
      return {
        cars: [
          { id: 1, brand: "Volkswagen", model: "Fox" },
          { id: 2, brand: "Volkswagen", model: "Golf" },
          { id: 3, brand: "Volkswagen", model: "Saveiro" },
          { id: 4, brand: "Volkswagen", model: "Gol" },
        ],
        lastIndex: 4,
      };
    },
    methods: {
      addCar(newCar) {
        this.cars.push(newCar);
        this.lastIndex += 1;
      },
      deleteCrr(index) {
        if (index !== -1)
          this.cars.splice(index, 1);
      }
    }
  };
</script>
