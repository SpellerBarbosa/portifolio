<script setup lang="ts">
import type { Project } from '~/models/model_projects';
import Aos from 'aos';
import 'aos/dist/aos.css';

const projetos: Project[] = [
    { 
        projeto: "Big Bang - Jokenpo", 
        imagem: "pedra_papel.png", 
        github: "https://github.com/SpellerBarbosa/game-jokenpo", 
        deploy: "https://spellerbarbosa.github.io/game-jokenpo/"
    },
    { 
        projeto: "Desafio - Ponte de Vidro", 
        imagem: "glass_bridge.png", 
        github: "https://github.com/SpellerBarbosa/glass_bridge", 
        deploy: "https://spellerbarbosa.github.io/glass_bridge/"},
    ]

onMounted(()=>{
    Aos.init();
})
</script>

<template>
    <section data-aos="fade-up" class="w-screen mt-[80px] flex flex-col items-center justify-center md:w-[70%] lg:w-[80%]" id="projetos">
        <h1 class="text-3xl uppercase font-semibold text-[#f4f4f5]">Projetos</h1>

        <ul  class="w-[100%] flex flex-wrap items-center justify-center gap-4 mt-10 text-lg font-medium text-[#f4f4f5] uppercase tracking-wider md:gap-10
        ">
            <li v-for="(projeto, index) in projetos" :key="index" class="w-[350px] h-[250px] flex flex-col items-center justify-evenly border rounded-xl bg-[#1e293b] border-[#1E293B] md:w-[450px] md:h-[350px]">
                <span class="w-[100%] h-[15%] grid place-items-center border-b-1 bg-[#1e293b] border-[#1E293B] rounded-xl">{{ projeto.projeto }}</span>
                <ul class="w-[100%] h-[85%] flex flex-col justify-evenly items-center">
                    <li class="w-[100%] border-b-1 bg-[#1e293b] border-[#1E293B]">
                        <img :src="`/img/${projeto.imagem}`" :alt="projeto.projeto" class="w-[98%] m-auto">
                    </li>
                    <li class="w-[calc(100%)] h-[20%] flex justify-evenly items-center">
                        <button class="w-[calc(100%/2)] h-[100%]"><a :href="projeto.github" target="_blank">GitHub</a></button>
                        <button class="w-[calc(100%/2)] h-[100%]"><a :href="projeto.deploy" target="_blank">deploy</a></button>
                    </li>
                </ul>
            </li>

        </ul>
    </section>
</template>