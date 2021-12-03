<template>
  <div id="app">
    <HeadingCalculation />
  </div>
</template>

<script>
import HeadingCalculation from './components/HeadingCalculation.vue';

export default {
  name: 'App',
  components: {
    HeadingCalculation,
  },
};
</script>

<style lang="scss">
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
</style>
