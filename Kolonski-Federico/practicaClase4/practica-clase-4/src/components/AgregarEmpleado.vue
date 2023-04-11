<template>
    <div class="form-floating mb-3">
        <input type="text" class="form-control" id="floatingInput" placeholder="Nombre" v-model="empleado.nombre">
        <label for="floatingInput">Nombre</label>
    </div>
    <div class="form-floating mb-3">
        <input type="text" class="form-control" id="floatingInput" placeholder="Apellido" v-model="empleado.apellido">
        <label for="floatingInput">Apellido</label>
    </div>
    <div class="form-floating mb-3">
        <input type="text" class="form-control" id="floatingInput" placeholder="Puesto" v-model="empleado.puesto">
        <label for="floatingInput">Puesto</label>
    </div>
    <button type="button" class="btn btn-success" @click="agregarEmpleado()">Agregar</button>
</template>

<script>
    export default {
        emits: ['agregarEmpleado'],  
        data() {
            return {
                empleado:
                    {
                        id: "",
                        nombre: "",
                        apellido: "",
                        puesto: ""
                    }
            };
        },
        methods: {
            agregarEmpleado() {
            this.$emit('agregarEmpleado',this.empleado);  
            },
        },
        };
</script>

<style>

</style>