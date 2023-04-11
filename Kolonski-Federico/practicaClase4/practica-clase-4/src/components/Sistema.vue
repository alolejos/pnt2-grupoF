<script setup>
    import TablaEmpleados from './TablaEmpleados.vue';
</script>

<template>
    <div class="layout">
        <h1>Base de datos - Empleados</h1>
        <TablaEmpleados />
    </div>
</template>


<style>
    .layout {
        display: flex;
        flex-direction: column;
    }
</style>