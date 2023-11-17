<script setup>
    const prop = defineProps(["description"]);

</script>

<template>
    <div>
        <h3>Username</h3>
        <p>{{description}}</p>
    </div>
</template>

<style scoped> /* scoped is enkel over deze pagina, je moet dus niet met classes sukkelen <div></div> */
    div{
        color: white
    }
</style>
