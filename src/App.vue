<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>

<script>
import Header from './components/layout/Header.vue';

export default {
  name: 'App',
  components: {
    Header
  }
}
  
</script>

<style>
html {
  box-sizing: border-box;
  font-size: 62.5%;
  margin: 0;
  padding: 0;
}

*, *::before, *::after {
  box-sizing: inherit;
}

body {
  font-size: 1.6rem;
  font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
  line-height: 1.4;
} 

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}

</style>
