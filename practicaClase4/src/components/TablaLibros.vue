<template>
  <table class="table table-striped text-center">
    <thead>
      <tr>
        <th>Nombre</th>
        <th>Autor</th>
        <th>Precio</th>
        <th>Opciones</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="libro in libros" :key="libro.id">
        <td>{{ libro.nombre }}</td>
        <td>{{ libro.autor }}</td>
        <td>{{ libro.precio }}</td>
        <td>
          <button class="btn-secondary" @click="generarHash()">Edit</button
          ><button class="btn-danger" @click="borrar(libro.id)">Delete</button>
        </td>
      </tr>
    </tbody>
  </table>
  <input v-model="nombre" placeholder="Nombre" />
  <input v-model="autor" placeholder="Autor" />
  <input v-model="precio" placeholder="Precio" />
  <button class="btn-primary" @click="agregar()">Agregar</button>
</template>

<script>
import { uuidv4 } from "vue-uuid";

export default {
  props: {
    libros: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      nombre: "",
      autor: "",
      precio: "",
    };
  },
  methods: {
    generarHash() {
      const uuid = uuidv4.v4();
      console.log(uuid);
      return uuid.toString();
    },
    agregar() {
      let libro = {
        id: this.generarHash(),
        nombre: this.nombre,
        autor: this.autor,
        precio: this.precio,
      };
      console.log(libro);
      this.libros.push(libro);
    },
  },
};
</script>

<style></style>
