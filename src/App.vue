<template>
  <div id="app">
    <HeaderComponent />
    <router-view></router-view>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent
  }
};
</script>

<style>
/* Aggiungi eventuali stili personalizzati qui */
</style>