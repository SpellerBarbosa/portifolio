<script setup lang="ts">
import { onMounted } from 'vue';
import TypeIt from 'typeit';

onMounted(()=>{
    new TypeIt("#typewriter",{
        speed: 50,
        waitUntilVisible: true,
    })
    .type("Olá, me chamo ")
    .pause(300)
    .type("<strong class='uppercase font-bold'>Fernando Barbosa</strong> ")
    .break()
    .pause(300)
    .type("e sou desenvolvedor ")
    .pause(300)
    .type("<strong class='uppercase font-bold'>Full Stack</strong>.")
    .go();
});
</script>

<template>
    <article class="w-[90%] mt-[100px] flex flex-col items-center">
        <h1  id="typewriter" class="text-2xl text-left bg-gradient-to-r from-[#F4F4F5] to-[#4F9EFF] bg-clip-text text-transparent tracking-[2px] capitalize mb-[20px]"></h1>
        <p>"Tecnologia é a ponte entre a ideia e a realização — do simples à inovação."</p>
    </article>
</template>