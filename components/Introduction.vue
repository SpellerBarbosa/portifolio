<script setup lang="ts">
import { ref, onMounted, nextTick } from 'vue';
import TypeIt from 'typeit';

const showQuote = ref(false);
const quoteRef = ref<HTMLElement | null>(null);
const buttonsRef = ref<HTMLElement | null>(null);

onMounted(() => {
    new TypeIt("#intro-headline", {
        speed: 35,
        waitUntilVisible: true,
    })
        .type("Olá, sou ")
        .pause(300)
        .type("<strong class='uppercase font-bold'>Fernando Barbosa, </strong>")
        .pause(500)
        .break()
        .type("um desenvolvedor ")
        .pause(300)
        .type("<strong class='uppercase font-bold'>Full Stack</strong> Em Formação.")
        .go();

    new TypeIt("#intro-description", {
        speed: 35,
        startDelay: 4500,
        waitUntilVisible: true,
        afterComplete: async () => {
            showQuote.value = true;
            await nextTick(); // garante que o DOM foi atualizado
            setTimeout(() => {
                quoteRef.value?.classList.add("opacity-100");
                buttonsRef.value?.classList.add("opacity-100");
            }, 50); // tempo mínimo para garantir transição
        }
    })
        .type("Este portfólio foi criado para compartilhar minha ")
        .pause(300)
        .type("<strong class='font-bold'>jornada como desenvolvedor</strong>, projetos e aprendizados.")
        .go();
});
</script>

<template>
    <article
        class="w-[90%] h-[350px]  mt-[100px] flex flex-col items-center text-center max-w-3xl mx-auto text-[#f4f4f5] bg-[#13171d] md:w-[70%] md:h-[40vh] md:justify-around lg:w-[80%]" id="home">
        <h1 id="intro-headline"
            class="text-2xl sm:text-3xl md:text-4xl bg-gradient-to-r from-[#F4F4F5] to-[#4F9EFF] bg-clip-text text-transparent tracking-[2px] capitalize font-semibold mb-4">
        </h1>

        <p id="intro-description" class="text-base sm:text-lg text-[#cbd5e1] mt-2 mb-6 px-2 md:text-xl"></p>

        <blockquote v-show="showQuote" ref="quoteRef"
            class="italic text-sm text-gray-400 opacity-0 transition-opacity duration-700 ease-in-out md:text-xl">
            "Tecnologia é a ponte entre a ideia e a realização — do simples à inovação."
        </blockquote>

        <section class="w-[100%]  flex justify-evenly mt-5 font-semibold opacity-0 transition-opacity duration-700 ease-in-out
        " ref="buttonsRef">
            <button class=" h-[50px] w-[150px] bg-[#1E293B] rounded-xl cursor-pointer hover:bg-[#3b82f6]" v-show="showQuote"><a href="#projetos">Ver Projetos</a></button>
            <button class=" h-[50px] w-[150px] bg-[#1E293B] rounded-xl cursor-pointer  hover:bg-[#3b82f6]" v-show="showQuote"><a href="https://drive.google.com/file/d/1Rg9qoQquNswv5kIE8y2G5ZzA80WeXCg0/view?usp=drive_link" target="_blank">Baixar CV</a></button>
        </section>
    </article>
</template>
