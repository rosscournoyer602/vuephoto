<template>
  <div id="app">
   <Photos />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Photos from './components/Photos.vue';

export default Vue.extend({
  name: 'App',
  components: {
    Photos
  }
});
</script>

<style>
</style>
