<template>
    <tr>
        <th scope="row">{{ detalle }}</th>
        <td>
            <div class="form-check form-switch">
                <input class="form-check-input" type="checkbox" role="switch" id="flexSwitchCheckDefault" @input="cambiarEstado({ detalle })">
                <button type="button" class="btn btn-danger" @click="eliminarTarea({ detalle })">Eliminar</button>
            </div>
        </td>
    </tr>
</template>

<script>
    export default {
        props: ['detalle','completado'],
        emits: ['cambiarEstado','eliminarTarea'],
        data() {
        },
        methods: {
            cambiarEstado(c) {
                this.$emit('cambiarEstado',c);  
            },
            eliminarTarea(c) {
                this.$emit('eliminarTarea',c);  
            }
        }
    }
</script>

<style>
</style>