<template>
  <div id="app">
    <MainSection title="Accueil" nextpage="projects"/>
    <MainSection title="Projects" />
    <MainSection title="Introduction"/>
  </div>
</template>

<script>
import MainSection from './components/MainSection.vue'

export default {
  name: 'App',
  components: {
    MainSection
  }
}
</script>

<style>
html, body {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  scroll-behavior: smooth;
}
body{
  display:flex;
}
#app {
  box-sizing: border-box;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  display: flex;
  flex-direction: column;
  margin: 0;
  padding: 0;
  border: 0;
  width: 100%;
}
</style>
