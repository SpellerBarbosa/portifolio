<script setup lang="ts">
import { ref, onMounted, nextTick } from 'vue';
import TypeIt from 'typeit';

const showQuote = ref(false);
const quoteRef = ref<HTMLElement | null>(null);
const buttonsRef = ref<HTMLElement | null>(null);

onMounted(() => {
    new TypeIt("#intro-headline", {
        speed: 50,
        waitUntilVisible: true,
    })
        .type("Olá, meu nome é ")
        .pause(300)
        .type("<strong class='uppercase font-bold'>Fernando</strong>")
        .pause(500)
        .break()
        .type("e estou aprendendo sobre ")
        .pause(300)
        .type("<strong class='uppercase font-bold'>desenvolvimento de software</strong>.")
        .go();

    new TypeIt("#intro-description", {
        speed: 40,
        startDelay: 6500,
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
        class="w-[90%] h-[450px] border-b-1 mt-[100px] flex flex-col items-center text-center max-w-3xl mx-auto text-[#f4f4f5]">
        <h1 id="intro-headline"
            class="text-2xl sm:text-3xl md:text-4xl bg-gradient-to-r from-[#F4F4F5] to-[#4F9EFF] bg-clip-text text-transparent tracking-[2px] capitalize font-semibold mb-4">
        </h1>

        <p id="intro-description" class="text-base sm:text-lg text-[#cbd5e1] mt-2 mb-6 px-2"></p>

        <blockquote v-show="showQuote" ref="quoteRef"
            class="italic text-sm text-gray-400 opacity-0 transition-opacity duration-700 ease-in-out">
            "Tecnologia é a ponte entre a ideia e a realização — do simples à inovação."
        </blockquote>

        <section class="w-[100%]  flex justify-evenly mt-2.5 font-semibold opacity-0 transition-opacity duration-700 ease-in-out
        " ref="buttonsRef">
            <button class=" h-[50px] w-[150px] bg-[#1E293B] rounded-xl cursor-pointer
            " v-show="showQuote">Ver Projetos</button>
            <button class=" h-[50px] w-[150px] bg-[#1E293B] rounded-xl cursor-pointer
            " v-show="showQuote">Baixar CV</button>
        </section>
    </article>
</template>
