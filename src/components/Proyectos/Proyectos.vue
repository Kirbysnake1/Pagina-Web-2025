<template>
    <section id="Proyectos">
        <div class="github-carousel">
            <h2 class="title">🚀 Mis proyectos en GitHub</h2>

            <Swiper :modules="[Autoplay, Pagination]" :slides-per-view="1" :space-between="20" :loop="true"
                :autoplay="{ delay: 3000 }" pagination class="carousel">
                <SwiperSlide v-for="repo in repos" :key="repo.id">
                    <div class="card">
                        <h3>{{ repo.name }}</h3>
                        <p>{{ repo.description || 'Sin descripción' }}</p>
                        <div class="meta">
                            ⭐ {{ repo.stargazers_count }} | 🍴 {{ repo.forks_count }}
                        </div>
                        <a :href="repo.html_url" target="_blank" class="link">
                            Ver proyecto
                        </a>
                        <br>
                    </div>
                </SwiperSlide>
            </Swiper>
        </div>

    </section>
</template>

<script setup>
import './Proyectos.css'

import { ref, onMounted } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, Pagination } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/pagination'

// ⚙️ Cambia por tu usuario de GitHub
const GITHUB_USER = 'Kirbysnake1'
const repos = ref([])

const cargarRepos = async () => {
    try {
        const res = await fetch(`https://api.github.com/users/${GITHUB_USER}/repos`)
        const data = await res.json()
        // Ordenar por última actualización
        repos.value = data.sort((a, b) => new Date(b.updated_at) - new Date(a.updated_at))
    } catch (error) {
        console.error('Error cargando repos:', error)
    }
}

onMounted(cargarRepos)
</script>
