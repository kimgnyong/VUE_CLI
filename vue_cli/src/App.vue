<template>
  <div id="app">
    <header-component></header-component>
    <input-component></input-component>
    <list-component></list-component>
    <footer-component></footer-component>
  </div>
</template>



<script>
import HeaderCompontnt from './components/HeaderCompontnt.vue'
import InputComponent from './components/InputComponent.vue'
import ListComponent from './components/ListComponent.vue'
import FooterComponent from './components/FooterComponent.vue'

export default {
  name: 'app',
  components:{
    'header-component' : HeaderCompontnt,
    'input-component' : InputComponent,
    'list-component' : ListComponent,
    'footer-component' : FooterComponent
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
