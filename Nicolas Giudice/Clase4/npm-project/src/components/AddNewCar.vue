<template>
  <h2>Agregar auto</h2>
  
  <form @submit.prevent="addCar">
    <div class="mb-2">
      <label>
        Marca:
        <input name="brand" />
      </label>
    </div>

    <div class="mb-2">
      <label>
        Modelo:
        <input name="model" />
      </label>
    </div>

    <button>Agregar</button>
  </form>

</template>

<script>
  export default {
    emits: ["addCarInList"],
    methods: {
      addCar(e) {
        const newCar = {
          id: this.lastIndex + 1,
          brand: e.target.brand.value,
          model: e.target.model.value,
        };

        this.$emit("addCarInList", newCar);
      }
    },
    props: ['lastIndex'],
    
  }
</script>

<style>
  .mb-2 {
    margin-bottom: 16px;
  }
</style>