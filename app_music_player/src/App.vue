<template>
  <div class="app-container p-3 bg-black rounded m-auto mt-2">
    <lista-de-sons/>
  </div>
  
</template>

<script>

  import ListaDeSons from './components/ListaDeSons.vue';

  export default {
    name: 'App',
    components: {
      ListaDeSons
    }
  }
</script>

<style>

  .app-container {
    width: 350px;
    height: 720px;
  }

</style>
