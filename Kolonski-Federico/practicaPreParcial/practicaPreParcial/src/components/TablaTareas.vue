<template>
    <div class="container">
        <table class="table table-striped table-hover">
            <thead>
                <tr>
                    <th scope="col">Tarea</th>
                    <th scope="col">Completado</th>
                </tr>
            </thead>
            <tbody>
                <ItemTabla
                    v-for="tarea in tareas"
                    :key="tarea.detalle"
                    v-bind:detalle="tarea.detalle" 
                    v-bind:completado="tarea.completado"
                    @cambiarEstado="cambiarEstado($event)"
                    @eliminarTarea="eliminarTarea($event)"
                />
            </tbody>
        </table>
        <Filtros
            @pendiente="pendiente($event)"
            @completado="completado($event)"
        />
        <AgregarTarea @agregarTarea="agregarTarea($event)"  />
    </div>
</template>

<script>
    import ItemTabla from './ItemTabla.vue';
    import AgregarTarea from './AgregarTarea.vue';
import Filtros from './Filtros.vue';
    export default {
        components: {
    ItemTabla,
    AgregarTarea,
    Filtros
},
        data() {
            return {
                tareas: [],
                tareasFiltradas: [],
                filtroCompletado: false,
                filtroPendiente: false
            }
        },
        methods: {
            agregarTarea(e) {
                this.tareas.push({...e})
            },
            eliminarTarea(e) {
                const nuevasTareas = this.tareas.filter(i => i.detalle !== e.detalle);
                this.tareas = nuevasTareas;
            },
            cambiarEstado(e) {
                const tarea = this.tareas.find(t => t.detalle === e.detalle);
                tarea.completado = !tarea.completado;
            },
            completado(e) {
                //PENDIENTE
            },
            pendiente(e) {
                //PENDIENTE
            }
        }
    }
</script>

<style>
    .container {
        display: flex;
        flex-direction: column;
        gap: 1em;
    }
</style>