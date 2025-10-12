<template>
  <section id="Bio">
    <br>
    <div class="container">

      <div class="c1">
        <img src='./../../assets/images/bio/peSoft.webp' />
      </div>

      <div class="c2">
        Hola! Soy Andres Ramirez, un <span id="typed-wrapper"><span id="typed"></span></span> de 20 años, vivo en
        Medellín, Colombia.<br>
        Creo en el poder transformador de la tecnología para hacer del mundo un lugar mejor.<br>
        Mi pasión por la innovación y el desarrollo de software me impulsa a buscar constantemente nuevas formas de
        crear soluciones impactantes.
        Mi objetivo es inspirar a otros a perseguir sus sueños y contribuir positivamente a la comunidad
        tecnológica, mientras sigo aprendiendo y creciendo en este emocionante viaje. <br> </br>

        <div class="img_Bio">
          <a target="_blank" href="https://www.linkedin.com/in/andres-ramirez-4a677023b/">
            <img src="../../assets/images/bio/LinKedin.webp" title="Linkedin" class="img_Bio">
          </a>
          <a target="_blank" href="https://github.com/Kirbysnake1">
            <img src="../../assets/images/bio/gitHub.webp" title="gitHub" class="img_Bio" />
          </a>
          <a target="_blank" href="https://www.instagram.com/andres16fell/">
            <img src="../../assets/images/bio/IG.webp" title="Instagram" class="img_Bio">
          </a>
        </div>
      </div>
    </div>
  </section>

</template>

<script setup>
import './Bio.css'

import { onMounted } from 'vue'

onMounted(() => {

  // 🔍 Depuración: muestra en consola las referencias de los elementos HTML
  console.log('typed:', document.getElementById('typed'));
  console.log('wrapper:', document.getElementById('typed-wrapper'));

  // 📌 Referencia al span donde se escribirá el texto dinámico
  const el = document.getElementById('typed')

  // ⚡ Aplica estilo solo a este span para que el texto no haga salto de línea
  el.style.whiteSpace = 'nowrap'

  // 📂 Palabras que se van a escribir con el efecto typewriter
  const words = ["Trainer Frontend", "Jr QA automatizador"]

  // 🔢 Variables de control para la animación
  let i = 0              // índice actual en el array de palabras
  let j = 0              // posición actual dentro de la palabra
  let currentWord = ''   // palabra parcial que se va construyendo
  let isDeleting = false // bandera para alternar entre escribir y borrar
  let speed = 30        // velocidad dinámica de escritura/borrado

  /**
   * 🖊️ Función principal del efecto typewriter
   * - Escribe carácter por carácter de cada palabra
   * - Luego borra carácter por carácter
   * - Alterna entre palabras en bucle infinito
   */
  function type() {
    if (i >= words.length) i = 0        // Reinicia índice si llega al final
    const fullWord = words[i]           // Palabra completa actual

    if (!isDeleting) {
      // ➕ Modo escritura: agrega un carácter más
      currentWord = fullWord.slice(0, j + 1)
      j++
      el.textContent = currentWord

      if (currentWord === fullWord) {
        // ✅ Palabra completa alcanzada → activar borrado
        isDeleting = true
        speed = 1000 // breve pausa antes de borrar
      } else {
        speed = 60 // velocidad normal al escribir
      }
    } else {
      // ➖ Modo borrado: elimina un carácter
      currentWord = fullWord.slice(0, j - 1)
      j--
      el.textContent = currentWord

      if (currentWord === '') {
        // 🚀 Palabra completamente borrada → pasar a la siguiente
        isDeleting = false
        i++
        speed = 500 // pausa más larga antes de empezar la siguiente
      } else {
        speed = 100 // velocidad más rápida al borrar
      }
    }

    // ⏱️ Llamada recursiva controlada por velocidad
    setTimeout(type, speed)
  }

  // ▶️ Inicializa el efecto typewriter
  type()

  // 🎨 Ajustes de estilo para el contenedor del texto animado
  const wrapper = document.getElementById('typed-wrapper')
  wrapper.style.display = 'inline-block'  // mantiene alineación con el texto base
  wrapper.style.whiteSpace = 'nowrap'     // evita saltos de línea dentro del wrapper
})

</script>