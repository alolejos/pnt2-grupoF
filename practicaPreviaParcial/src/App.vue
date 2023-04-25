<script>
export default {
  data() {
    return {
      lista: [],
      todo: {
        id: "",
        nombre: "",
        descripcion: "",
        fechaVencimiento: "",
        hecho: false,
      },
    };
  },
  methods: {
    agregar(todo) {
      this.lista.push({ ...todo });
    },
    hecho(id) {
      let index = this.lista.findIndex((n) => n.id == id);
      if (index != -1) this.lista[index].hecho = true;
    },
  },
};
</script>

<template>
  <div class="row">
    <div class="col-md 3">
      <h1>Ingrese la tarea</h1>
      <form>
        <div class="mb-3">
          <label for="nombre" class="form-label">Nombre</label>
          <input
            v-model="todo.nombre"
            type="text"
            class="form-control"
            id="nombre"
            aria-describedby="nombreAyuda"
          />
          <div id="nombreAyuda" class="form-text">
            Ingrese el nombre de la tarea
          </div>
        </div>
        <div class="mb-3">
          <label for="descripcion" class="form-label">Descripción</label>
          <input
            v-model="todo.descripcion"
            type="text"
            class="form-control"
            id="descripcion"
            aria-describedby="descripcionAyuda"
          />
          <div id="descripcionAyuda" class="form-text">
            Ingrese una breve descripción de la tarea
          </div>
        </div>
        <div class="mb-3">
          <label for="exampleInputPassword1" class="form-label"
            >Vencimiento</label
          >
          <input
            v-model="todo.fechaVencimiento"
            type="date"
            class="form-control"
            id="exampleInputPassword1"
          />
        </div>
        <button v-on="guardar(todo)" type="submit" class="btn btn-primary">
          Agregar
        </button>
      </form>
    </div>
    <div class="col-md-9">
      <div>
        <h1>Listado</h1>
        <table class="table">
          <thead>
            <tr>
              <th scope="col">#</th>
              <th scope="col">Nombre</th>
              <th scope="col">Vencimiento</th>
              <th scope="col">Opciones</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(hacer, index) in lista">
              <th v-if="!hacer.hecho" scope="row">{index}</th>
              <td v-if="!hacer.hecho">{hacer.nombre}</td>
              <td v-if="!hacer.hecho">{hacer.fechaVencimiento}</td>
              <td v-if="!hacer.hecho">
                <button @click="hecho(hacer.id)" class="btn btn-warning">
                  Hecho</button
                ><button @click="borrar(hacer.id)" class="btn btn-danger">
                  Borrar
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<style></style>
