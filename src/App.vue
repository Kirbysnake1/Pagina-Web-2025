<script setup>
import Header from './components/Header/Header.vue'
import Bio from './components/Bio/Bio.vue'
import Experiencia from './components/Experiencia/Experiencia.vue'
import Proyectos from './components/Proyectos/Proyectos.vue'
import Footer from './components/Footer/Footer.vue'
</script>

<template>
  <div class="app-container">
    <Header/> 
    <main class="content">
      <Bio/>
      <Experiencia/>
      <Proyectos/>
    </main>

    <br><br><br><br><br><br><br><br>

    <Footer/>
  </div>
</template>

<style>
html, body, #app {
  margin: 0;
  padding: 0;
  width: 100vw;
  overflow-x: hidden;
}

body {
  background: #F5F7FA;
  font-family: 'Open Sans', sans-serif;
}

.main {
  width: 100%;
}
</style>