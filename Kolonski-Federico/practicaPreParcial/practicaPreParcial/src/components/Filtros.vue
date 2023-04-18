<template>
    <div class="filtros">
        <span>Pendientes</span>
        <div class="form-check form-switch">
            <input class="form-check-input" type="checkbox" role="switch" id="flexSwitchCheckDefault" @input="pendiente()">
        </div>
    </div>
    <div class="filtros">
        <span>Completadas</span>
        <div class="form-check form-switch">
            <input class="form-check-input" type="checkbox" role="switch" id="flexSwitchCheckDefault" @input="completado()">
        </div>
    </div>
</template>

<script>
    export default {
        emits: ['pendiente','completado'],
        data() {
            return {
                filtroPendiente: false,
                filtroCompletado: false
            }
        },
        methods: {
            pendiente() {
                this.filtroPendiente = !this.filtroPendiente;
                this.$emit('pendiente',this.filtroPendiente);  
            },
            completado() {
                this.filtroCompletado = !this.filtroCompletado;
                this.$emit('completado',this.filtroCompletado);  
            }
        }
    }
</script>

<style>
.filtros {
    display: flex;
    flex-direction: row;
    gap: .4em;
}
</style>