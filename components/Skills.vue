<script setup lang="ts">
import AOS from "aos";
import "aos/dist/aos.css";

const imagens: string[] = [
  "css.png",
  "html.png",
  "js.png",
  "mongodb.png",
  "node.png",
  "nuxt.png",
  "tailwind.png",
  "vue.png",
];

onMounted(() => {
  AOS.init();
});
</script>

<template>
  <section
    class="mt-[60px] w-screen text-[#f4f4f5] flex flex-col items-center tracking-[1.5px] font-semibold md:w-[70%] lg:w-[50%]"
    data-aos="fade-up"
    id="habilidades"
  >
    <h1 class="text-3xl p-6 uppercase">habilidades</h1>

    <ul class="w-[100%] flex gap-4 flex-wrap items-center justify-center md:gap-10">
      <li
        v-for="(imagem, index) in imagens"
        :key="index"
        class="w-[100px] h-[100px] grid place-items-center uppercase font-semibold tracking-[1px] text-[#f4f4f5] bg-[#1e293b] border-[#1E293B] hover:scale-115 rounded-lg md:w-[180px] md:h-[180px]"
      >
        <img
          :src="`/img/${imagem}`"
          :alt="imagem.split('.')[0]"
          class="w-[60%]"
        />
        <span>{{ imagem.split(".")[0] }}</span>
      </li>
    </ul>
  </section>
</template>
