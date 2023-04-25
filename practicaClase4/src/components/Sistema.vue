<template>
  <div>
    <Cabecera />
    <h1>Gestor de Libros</h1>
    <TablaLibros :libros="libros"></TablaLibros>
    <Libros @agregarPadre="agregar($event)" />
    <Pie v-bind:autor="autor" />
  </div>
</template>

<script>
import Cabecera from "./Cabecera.vue";
import Pie from "./Pie.vue";
import Item from "./Item.vue";
import Libros from "./Libros.vue";
import TablaLibros from "./TablaLibros.vue";
export default {
  components: {
    Cabecera,
    Pie,
    Item,
    Libros,
    TablaLibros,
  },
  data() {
    return {
      autor: "Cualquier otro",
      libros: [
        { id: 1, nombre: "Libro de la Selva", autor: "Ni Idea", precio: 10 },
        { id: 2, nombre: "Alicia", autor: "Lewis Carroll", precio: 20 },
      ],
    };
  },
  methods: {
    agregar(libritoRecibido) {
      this.libros.push({ ...libritoRecibido });
    },
  },
};
</script>

<style></style>
