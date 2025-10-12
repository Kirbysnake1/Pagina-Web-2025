<template>
    <section id="Experiencia">
        <h1 class="h1_exp">Experiencia</h1>
        <div class="slider">
            <div class="item">
                <h1 class="h1_exp_box">Analista QA Manual</h1>
                <h4 class="h4_exp_box">TCS-Citybank (Jun/2023 - Ene/2024) <br>6 meses</h4>
                <p class="p_exp_box">
                    <strong>Tareas realizadas durante mi etapa laboral:</strong><br>
                    - Pruebas de Funcionalidad <br></br>
                    - Pruebas de Seguridad<br></br>
                    - Documentación de Pruebas<br></br>
                    - Pruebas de Integración<br>
                    - Experiencia en el Sector Bancario <br></br>
                    - Realización de Pruebas smoke <br></br>
                    - Manejo de Jira <br></br>
                    - Manejo de Ambientes SIT/UAT <br></br>
                    - Manejo de Base de Datos <br></br>
                    - Marco metodologia Scrum <br></br>
                    <br></br>
                    <strong>Red empresarial de empresa:</strong><br>
                    <a href="https://www.linkedin.com/company/tata-consultancy-services/" target="_blank">TCS</a>
                </p>
            </div>

            <div class="item">
                <h1 class="h1_exp_box">Analista QA Automatizador</h1>
                <h4 class="h4_exp_box">Virtualsoft (Ene/2024 - actualidad) <br> 1 año 4 meses</h4>
                <p class="p_exp_box">
                    <strong>Tareas realizadas durante mi etapa laboral:</strong><br>
                    - Exp en Sector apuestas deportivas y casinos virtuales <br>
                    - Automatizacion de flujos con Cypress/Playwright <br>
                    - Realización de Documentación de HUs <br>
                    - Realizacion de Casos de prueba <br>
                    - Manejo de Documentacion Mediante Xray <br>
                    - Manejo de Documentación por Excel y Word <br>
                    - Reportes de Bugs y documentación de los mismos a traves de Jira <br>
                    - Manejo y validaciones en Ramas de Desarrollo y Produccion <br>
                    - Validacion de pruebas y funciones a traves de aplicacion de Postman <br>
                    <strong>Red empresarial de empresa:</strong><br>
                    <a href="https://www.linkedin.com/company/virtualsoft-servicios-y-software/"
                        target="_blank">VirtualSoft</a>
                </p>
            </div>
            <button id="next">></button>
            <button id="prev"><</button>
        </div>
    </section>
</template>

<script setup>
import "./Experiencia.css"
import { onMounted } from 'vue'

/**
 * @file Experiencia.vue
 * @description Componente Vue que muestra un slider con animación 3D de tarjetas de experiencia.
 * Incluye navegación mediante botones "Next" y "Prev".
 * Los efectos visuales se aplican dinámicamente con transformaciones CSS.
 */

/**
 * Inicializa el slider cuando el componente es montado.
 * 
 * - Define el estado `active` para controlar el slide actual.
 * - Aplica transformaciones 3D para dar efecto de profundidad.
 * - Controla la navegación entre slides mediante botones.
 * 
 * @function
 * @returns {void}
 */
onMounted(() => {
    /** @type {NodeListOf<HTMLElement>} Lista de elementos que representan los slides */
    const items = document.querySelectorAll('.slider .item')

    /** @type {HTMLElement|null} Botón de siguiente */
    const next = document.getElementById('next')

    /** @type {HTMLElement|null} Botón de anterior */
    const prev = document.getElementById('prev')

    /** @type {number} Índice del slide actualmente activo */
    let active = 0

    /**
     * Renderiza la posición y transformación de los elementos del slider.
     * 
     * - El slide activo se muestra al frente.
     * - Los slides siguientes y anteriores se desplazan con un efecto de profundidad.
     * 
     * @function loadShow
     * @returns {void}
     */
    function loadShow() {
        let stt = 0

        // Reinicia los estilos antes de aplicar transformaciones
        items.forEach(item => {
            item.style.transform = ''
            item.style.zIndex = ''
            item.style.filter = ''
            item.style.opacity = ''
        })

        // Slide activo (centro)
        items[active].style.transform = 'none'
        items[active].style.zIndex = 1
        items[active].style.filter = 'none'
        items[active].style.opacity = 1

        // Slides siguientes
        for (let i = active + 1; i < items.length; i++) {
            stt++
            items[i].style.transform = `translateX(${120 * stt}px) scale(${1 - 0.2 * stt}) perspective(16px) rotateY(-1deg)`
            items[i].style.zIndex = -stt
            items[i].style.filter = 'blur(5px)'
            items[i].style.opacity = stt > 2 ? 0 : 0.6
        }

        // Slides anteriores
        stt = 0
        for (let i = active - 1; i >= 0; i--) {
            stt++
            items[i].style.transform = `translateX(${-120 * stt}px) scale(${1 - 0.2 * stt}) perspective(16px) rotateY(1deg)`
            items[i].style.zIndex = -stt
            items[i].style.filter = 'blur(5px)'
            items[i].style.opacity = stt > 2 ? 0 : 0.6
        }
    }

    // Carga inicial del slider
    loadShow()

    /**
     * Avanza al siguiente slide.
     * 
     * @event click
     */
    next.onclick = function () {
        active = (active + 1) % items.length
        loadShow()
    }

    /**
     * Retrocede al slide anterior.
     * 
     * @event click
     */
    prev.onclick = function () {
        active = (active - 1 + items.length) % items.length
        loadShow()
    }
})
</script>
