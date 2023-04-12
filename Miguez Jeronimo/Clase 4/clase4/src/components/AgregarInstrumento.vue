<template>
    <form @submit.prevent="agregarInstrumento">
    <label>
        Tipo:
        <input name="tipo"/>
    </label>
    <label>
        Modelo:
        <input name="modelo"/>
    </label>

    <button class="eliminar">Agregar</button>
    </form>
</template>

<script>
export default {
    emits: ["agregarInst"],
    methods: {
        agregarInstrumento(e) {
            const newInst = {
                id: this.instrumento.length +1,
                tipo: e.target.tipo.value,
                modelo: e.target.modelo.value
            };
            this.$emit("agregarInst", newInst);
        }
    },
    props: ['instrumento']
}
</script>