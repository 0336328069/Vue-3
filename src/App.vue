<template>
  <hearder />
  <RouterView />
</template>

<script>
  import { RouterLink, RouterView } from 'vue-router';
  import Hearder from './components/header.vue'
  export default {
    components: {
      Hearder
    },
    setup() {
      
    },
  }
</script>

