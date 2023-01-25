<template>
  <div id="app">
    <MainSection title="Portfolio" nextpage="projects"/>
    <MainSection title="Projects" />
    <MainSection title="A Propos" v-on:mouseenter="createSpan()" :enterpage="InAProposPage"/>
    <MainSection title="Competences"/>
  </div>
</template>

<script>
import MainSection from './components/MainSection.vue'

export default {
  name: 'App',
  components: {
    MainSection
  },
  data(){
    return{
      IsPortfolioOpen : false,
      InAProposPage : false
    }
  },
  methods:{
    createSpan : function(){
      console.log('hello')
      this.InAProposPage = true
    }
  }
}
</script>

<style>

@font-face {
    font-family: "BigJohn";  
    src: local("BigJohn"), url(./assets/fonts/BigJohn-Bold.otf) format("opentype");
}

html, body {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  scroll-behavior: smooth;
  scroll-snap-type: y mandatory;
}
html{
  overflow-y: hidden;
}
body{
  display:flex;
}
#app {
  box-sizing: border-box;
  font-family: "BigJohn", Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  display: flex;
  flex-direction: column;
  margin: 0;
  padding: 0;
  border: 0;
  width: 100%;

  scroll-snap-type: y mandatory;	
	-webkit-overflow-scrolling: touch;
}

</style>
