<template>
  <div class="app" id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="scss">
  @import 'reset-css/reset.css'; // Eric Meyer's CSS reset

  // Bootstrap
  @import 'bootstrap/dist/css/bootstrap-grid.min.css';

  // Base app styles
  @import 'scss/app';
</style>
