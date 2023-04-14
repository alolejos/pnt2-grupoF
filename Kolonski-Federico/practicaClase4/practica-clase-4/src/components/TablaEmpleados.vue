<template>
    <table class="table table-striped table-hover">
    <thead>
        <tr>
        <th scope="col">Id</th>
        <th scope="col">Nombre</th>
        <th scope="col">Apellido</th>
        <th scope="col">Puesto</th>
        </tr>
    </thead>
    <tbody>
        <ItemTabla
            v-for="empleado in empleados"
            :key="empleado.id"
            v-bind:id="empleado.id" 
            v-bind:nombre="empleado.nombre" 
            v-bind:apellido="empleado.apellido" 
            v-bind:puesto="empleado.puesto" 
        />
    </tbody>
    </table>
    <AgregarEmpleado @agregarEmpleado="agregarEmpleado($event)"  />
</template>

<script>
    import ItemTabla from './ItemTabla.vue';
    import AgregarEmpleado from './AgregarEmpleado.vue';
    import { uuid } from 'vue-uuid';
    export default {
        components: {
            ItemTabla,
            AgregarEmpleado
        },
        data() {
            return {
                empleados: [
                    {
                        id: 1,
                        nombre: "Federico",
                        apellido: "Kolonski",
                        puesto: "Gerente"
                    },
                    {
                        id: 2,
                        nombre: "Juan",
                        apellido: "Perez",
                        puesto: "Operador"
                    }
                ]
            }
        },
        methods: {
            agregarEmpleado(e) {
                e.id = uuid.v4()
                this.empleados.push({...e})
            }
        }
    }
</script>
