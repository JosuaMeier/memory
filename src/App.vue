<template>
  <v-app>
    <div class="background"></div>
    <Memory/>
  </v-app>
</template>

<script>
import Memory from './components/Memory'

export default {
  name: 'App',
  components: {
    Memory
  }
}
</script>

<style scoped>
  .background {
    content: "";
    background: url('./assets/background.jpg');
    opacity: 0.3;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    position: absolute;
  }
</style>