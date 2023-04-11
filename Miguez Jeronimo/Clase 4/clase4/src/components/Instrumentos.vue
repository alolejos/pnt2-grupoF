<template>
<table>
<tr v-for="instrumento in instrumento">
    <td>{{instrumento.id}}</td>
    <td>{{instrumento.tipo}}</td>
    <td>{{instrumento.modelo}}</td>
    <td>
        <button @click="borrarInstrumento(instrumento.id)">Eliminar</button>
    </td>
</tr>
</table>

</template>

<script>
export default {
    props: ['instrumento'],
    emits: ['borrarInstrumento'],
    methods: {
        borrarInstrumento(id) {
            const index = this.instrumento.findIndex(instrumento => id ==instrumento.id)
            this.$emit('borrarInstrumento', index);


        }
    }
};

</script>
