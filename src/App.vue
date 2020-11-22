<template>
  <Header/>
  <Main/>
  <Footer/>
</template>

<script>
import Header from './components/Header/Header.vue'
import Footer from './components/Footer/Footer.vue'
import Main from './components/Main/Main.vue'

export default {
  name: 'App',
  components: {
    Header, Main, Footer
  }
}
</script>

<style>
#app {
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  overflow-x: hidden;
}

.sub_header {
  color: rgb(0, 0, 0);
  font-weight: 600;
  font-size: 24px;
  text-align: left;
  margin-top: 30px;
  margin-bottom: 30px;
  margin-left: 80px;
  letter-spacing: 1px;
  word-spacing: 1px;
}

body {
  margin: 0;
}
</style>
