<template>
    <div>
        <app-server-status v-for="server in 2" :nextID="loopID++"></app-server-status>
    </div>
</template>

<script>
    import ServerStatus from './ServerStatus.vue'
    export default {
        data(){
          return {
              loopID: 1
          }
        },
        components: {
            'app-server-status': ServerStatus
        }
    }

</script>