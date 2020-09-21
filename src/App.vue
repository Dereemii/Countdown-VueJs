<template>
  <div id="app" class="text-center">
   <h1 class="mb-3">{{ message }}</h1> 
    <contador></contador>
  </div>
</template>

<script>
import Contador from "./componentes/Contador.vue"
  export default {
    data() {
      return {
        message: 'Cuenta atrás',
      };
    },
    components: {Contador},
    methods:{

    }
  }
</script>

<style >
  body{
    color: lightgoldenrodyellow;
    background: rgb(2,0,36);
    background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(103,9,121,1) 58%, rgba(0,212,255,1) 100%);
  }
</style>