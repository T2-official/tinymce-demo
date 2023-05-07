<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App" />
  <tinymce v-model="value"></tinymce>
  {{ value }}
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import tinymce from './components/tinymce/index.vue'

export default {
  name: 'App',
  data() {
    return {
      value: 'New Content'
    };
  },
  components: {
    HelloWorld,
    tinymce
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
