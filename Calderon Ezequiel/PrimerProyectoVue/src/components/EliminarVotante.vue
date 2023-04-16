<template>
     

    <button @click="eliminar">Eliminar  </button>
    <input v-model="dni">
    <label >Dni</label>
</template>

<script>
    export default {
        emits: ['eliminarUltimo'],  
        data() {
            return {
                dni:""
            };
        },
        methods: {
            eliminar() {
               if(this.dni != ""){
                this.$emit('eliminarUltimo',this.dni);  
               }
                    
           
            },
        },
        };
</script>