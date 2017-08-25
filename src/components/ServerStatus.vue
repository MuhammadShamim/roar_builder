<template>
    <div>
        <h1>Server {{nextID}} / {{ prj }}</h1>
        <hr>
        <button @click="changeStatus">Change</button>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                prj: 'RB!'
            }
        },
        props: ['nextID'],
        methods: {
            changeStatus() {
                this.prj = 'New Builder';
            }
        }
    }
</script>

<style scoped>
    div {
        border: 2px solid #87ff14;
    }
</style>