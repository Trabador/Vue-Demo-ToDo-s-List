<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>

<script>
import Header from './components/Header'

export default {
  name: "App",
  components: {
    Header
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 5;
    padding: 0;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
</style>
