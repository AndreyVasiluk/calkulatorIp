<template>
    <div>
        <span v-for="(n, i) in dataIp" v-bind:key="i">{{ n }} </span>

    </div>
</template>

<script>
    export default {
        name: "NewListIp",
        props: ['dataIp'],
    }
</script>

<style scoped>
    span{
        display: block;
        text-align: left;
    }
</style>