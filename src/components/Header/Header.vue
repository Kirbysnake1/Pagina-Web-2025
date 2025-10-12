<template>
  <div class="header">
    <a href="#" @click.prevent="scrollToSection('Bio')">Bio 💻</a>
    <a href="#" @click.prevent="scrollToSection('Experiencia')">Experiencia 🌐</a>
    <a href="#" @click.prevent="scrollToSection('Proyectos')">Proyectos 📖</a>
    <a href="#" @click.prevent="scrollToSection('Footer')">Contacto 🤳</a>
  </div>
</template>

<script setup>
import './Header.css'

const scrollToSection = (id) => {
  const section = document.getElementById(id)
  if (section) {
    section.scrollIntoView({ behavior: 'smooth' })
  }
}

</script>
