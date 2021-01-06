<template>
    <div>
        <h1>{{ title }}</h1>
    </div>
</template>

<script>
export default {
    props:{
        title: String,
    }
}
</script>

<style scoped>
    h1{
        color: red;
        text-align: center;
        background-color: yellow;
        padding: 30px;
    }
</style>