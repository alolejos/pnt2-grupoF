<template>

<div class="form-floating mb-3">
        <input  v-model="votante.dni">
        <label >Dni</label>
    </div>
    <div class="form-floating mb-3">
        <input  v-model="votante.nombre" >
        <label >nombre</label>
    </div>
    <button @click="agregar">Agregar</button>

</template>


<script>
    export default {
        emits: ['agregarVotante'],  
        data() {
            return {
                votante:
                    {
                        dni:"",
                        nombre:"",
                    }
            };
        },
        methods: {
            agregar() {
                if(this.votante.dni!="" && this.votante.nombre != ""){

                    this.$emit('agregarVotante',this.votante);  

                }
           
            },
        },
        };
</script>
 