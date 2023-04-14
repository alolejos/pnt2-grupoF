<template>
  <table>
    <tr v-for="car in cars">
      <td>{{ car.id }}</td>
      
      <td>{{ car.brand }}</td>
      
      <td>{{ car.model }}</td>
      
      <td>
        <button @click="deleteCar(car.id)">Eliminar</button>
      </td>
    </tr>
  </table>
</template>

<script>
  export default {
    emits: ["deleteCarOfList"],
    methods: {
      deleteCar(id) {
        const index = this.cars.findIndex((car) => car.id === id);
        this.$emit("deleteCarOfList",index);
      },
    },
    props: ['cars'],
  };
</script>
