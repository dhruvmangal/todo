<template>
    <header>
        <h3>{{msg}}</h3>
    </header>
</template>

<style scoped>
header{
    background-color: white;
    color: #000;
    border: 1px solid #f1f1f1;
    padding: 10px;
    margin-bottom: 20;
}
</style>

<script>
export default {
    name : 'Header',
    props:{
        msg: String
    }
}
</script>