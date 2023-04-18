<template>
        <div class="form-floating mb-3">
            <input type="text" class="form-control" id="floatingInput" placeholder="Tarea" v-model="tarea.detalle">
            <label for="floatingInput">Agregar tarea</label>
            <button type="button" class="btn btn-success" @click="agregarTarea()">Agregar</button>
        </div>
</template>

<script>
    export default {
        emits: ['agregarTarea'],  
        data() {
            return {
                tarea:
                    {
                        detalle: "",
                        completado: false
                    }
            };
        },
        methods: {
            agregarTarea() {
                this.$emit('agregarTarea',this.tarea);  
            },
        },
        };
</script>

<style>
    .form-floating {
        display: flex;
        justify-content: center;
        flex-direction: column;
        gap: .5em;
    }
</style>