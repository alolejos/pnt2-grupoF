<template>
<!--   Desarrollar una aplicación web simple, utilizando Vue.js y Javascript para el frontend.
El desarrollo deberá ser versionado con git.
La aplicación a desarrollar consistirá en un formulario para crear y visualizar una lista de tareas (to-do list). Los usuarios deberán poder agregar tareas, marcarlas como completadas y eliminarlas. Además, la aplicación deberá tener un botón para filtrar las tareas por estado (completadas o pendientes).
Deberán usar definición de variables, arrays con sus métodos y directivas de Vue. -->
  
  <h1>
    To-Do List
  </h1>

  <form @submit.prevent="addTask" class="form-container">
    <div class="form-group">
      <label for="task">Tarea:</label>
      <input type="text" id="name" v-model="newTask.name">
    </div>
  
    <div class="form-group">
      <label for="description">Descripción:</label>
      <textarea id="description" v-model="newTask.description"></textarea>
    </div>
  
    <button type="submit" class="btn">Agregar tarea</button>
  </form>
  
  <table>
    <tr>
      <td>Tarea</td>
      <td>Descripcion</td>
      <td @click="changeFilter()">Estado <span>({{this.statusFilter}})</span></td>
      <td>Acciones</td>
    </tr>
    <tr v-for="task in filteredTasks" :key="task.id">
      <td>{{ task.name }}</td>
      <td>{{ task.description }}</td>
      <td v-bind:class="task.completed ? 'complete' : 'incomplete'">{{task.completed ? 'Completa' : 'Incompleta' }}</td>
      <td>
        <button @click="() => modifyStatus(task)">{{!task.completed ? 'Completa' : 'Incompleta' }}</button>
        <button class="delete" @click="() => deleteTask(task)">Eliminar</button>
      </td>
    </tr>
  </table>
  
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      newTask: {
        name: '',
        description: '',
        completed: false
      },
      tasks: [
        {name: 'Hacer TP', description: 'Completar TP de PNT2', completed: true},
        {name: 'Cocinar', description: 'Preparar la cena', completed: false},
        {name: 'Lavar', description: 'Lavar platos', completed: false},
        {name: 'Subir TP', description: 'Subir TP a Git', completed: true},
      ],
      filteredTasks: [],
      statusFilter: "Todos"
    }
  },
  mounted() {
    this.filteredTasks = [...this.tasks]
  },
  methods: {
    addTask() {
      this.tasks.push(this.newTask)
      this.newTask = {
        name: '',
        description: '',
        completed: false
      }
      this.filteredTasks = [...this.tasks];
    },
    deleteTask(task) {
      const index = this.tasks.indexOf(task);
      if (index !== -1) {
        this.tasks.splice(index, 1);
        this.filteredTasks = [...this.tasks];
      }
    },
    modifyStatus(task){
      task.completed = !task.completed;
    },
    changeFilter() {
      switch (this.statusFilter) {
        case 'Todos':
          this.statusFilter = "Completos";
          this.filteredTasks = [...this.tasks].filter(t => t.completed === true)
          break;
        case 'Completos':
          this.statusFilter = "Incompletos";
          this.filteredTasks = [...this.tasks].filter(t => t.completed === false)
          break;
        default:
          this.statusFilter = "Todos";
          this.filteredTasks = [...this.tasks];
          break;
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

table, th, td {
  margin: 0 auto;
  padding: 10px;
  border: 1px solid black;
  border-collapse: collapse;
}

td span{
  color: goldenrod;
  cursor: pointer;
}

td button:first-of-type{
  margin-right: 5px;
}

.form-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 2rem auto;
  padding: 2rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f5f5f5;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  max-width: 500px;
}

.form-group {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
}

.delete{
  background-color: crimson;
}

.complete{
  background-color: aquamarine;
}

.incomplete{
  background-color: indianred;
}


label {
  font-weight: bold;
  margin-bottom: 0.5rem;
}

input,
textarea {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 3px;
  font-size: 1rem;
  width: 100%;
  resize: none;
}

button {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 3px;
  background-color: gold;
  font-size: 1rem;
  transition: .3s ease-in-out;
  cursor: pointer;
  border: 1px solid black;
}

button:hover {
  background-color: transparent;
}

</style>
