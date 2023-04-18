<script setup>

</script>

<template>
    <!-- Desarrollar una aplicación web simple, utilizando Vue.js y Javascript 
    para el frontend. El desarrollo deberá ser versionado con git.
    La aplicación a desarrollar consistirá en un formulario para crear y visualizar 
    una lista de tareas (to-do list). Los usuarios deberán poder agregar tareas, 
    marcarlas como completadas y eliminarlas. Además, la aplicación deberá tener un 
    botón para filtrar las tareas por estado (completadas o pendientes).
    Deberán usar definición de variables, arrays con sus métodos y directivas de Vue. -->
  <header>
    

  </header>

  <main>
    <div>
      <h3>Filtrar por:</h3>

      <select v-model="filter">
        <option value="all">all</option>
        <option value="completed">completed</option>
        <option value="pending">pending</option>
      </select>
    </div>

    <table>
      <thead>
        <tr>
          <td>Estado</td>
          <td>Tarea</td>
          <td>Acciones</td>
        </tr>
      </thead>

      <tbody>
        <tr v-for="item in filteredList">
          <td>
            {{ item.status }}
          </td>

          <td>
            {{ item.task }}
          </td>

          <td>
            <button @click="updateStauts(item)" v-if="item.status === 'pending'">
              Marcar como completado
            </button>
            
            <button @click="updateStauts(item)" v-else>
              Marcar como pendiente
            </button>

            <button @click="deleteTask(item.id)" type="submit">Eliminar</button>
          </td>
          
        </tr>
      </tbody>
    </table>

    <div>
      <h2>Agregar nueva tarea</h2>

      <input v-model="inputTask" />
      <button @click="addTask">Agregar</button>
    </div>
  </main>
</template>

<script>
  export default {
    data() {
      return {
        filter: "all", 
        filteredList: [],
        inputTask: "",
        lastId: 0,
        list: [
          {
            id: 1,
            status: "pending",
            task: "item 1",
          },
          {
            id: 2,
            status: "completed",
            task: "item 2",
          },
          {
            id: 3,
            status: "pending",
            task: "item 3",
          }
        ],
      };
    },
    methods: {
      addTask() {
        this.lastId += 1;

        this.list.push({
          id: this.lastId,
          status: "pending",
          task: this.inputTask,
        });
      },
      deleteTask(id) {
        const index = this.list.findIndex((item) => item.id === id); 

        if (index !== -1) {
          this.list.splice(index, 1);
        }
      },
      updateStauts(listItem) {        
        const objTrasform = {
          completed: "pending",
          pending: "completed",
        };

        listItem.status = objTrasform[listItem.status];
      }
    },
    mounted() {
      this.filteredList = this.list;
      this.lastId = this.list.length;
    },
    watch: {
      filter(newValue, oldValue) {
        if (newValue === "all") {
          this.filteredList = this.list;    
        } else {
          this.filteredList = this.list.filter((item) => item.status === newValue);
        }
      }
    }
  }
</script>

<style scoped>

</style>