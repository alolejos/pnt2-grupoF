<template>
    <tr>
        <th scope="row">{{ id }}</th>
        <td>{{ nombre }}</td>
        <td>{{ apellido }}</td>
        <td>{{ puesto }}</td>
    </tr>
</template>

<script>
    export default {
        props: ['id','nombre','apellido','puesto'],
        data() {
            return {

            }
        }
    }
</script>

<style>
</style>