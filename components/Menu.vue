<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";

const mobile = ref<boolean>(true);
const nome = ref<string>("");
const stateMenu = ref<boolean>(true);
const menuRef = ref<HTMLElement | null>(null);

const toogleMenu = () => {
  stateMenu.value = !stateMenu.value;
};

const handerClickOutSide = (Event: MouseEvent) => {
  if (menuRef.value && !menuRef.value.contains(Event.target as Node)) {
    stateMenu.value = true;
  }
};

const checkWindowSize = () => {
  mobile.value = window.innerWidth <= 768;
  nome.value = mobile.value ? "F.B" : "Fernando Barbosa";
};

watchEffect(() => {
  onMounted(() => {
    document.addEventListener("click", handerClickOutSide);
    checkWindowSize();
    window.addEventListener("resize", checkWindowSize);
  });

  onUnmounted(() => {
    document.removeEventListener("click", handerClickOutSide);
    window.removeEventListener("resize", checkWindowSize);
  });
});
</script>

<template>
  <header
    :class="[
      mobile
        ? 'w-screen h-[60px] flex items-center justify-center text-[#f4f4f5] font-inter bg-[#1e293b] z-10 fixed'
        : 'md:flex-row-reverse',
      'w-screen h-[60px] flex flex-row-reverse justify-center items-center text-[#f4f4f5] uppercase tracking-[1px] md:justify-around bg-[#1e293b] fixed z-10 lg:h-[80px]',
    ]"
  >
    <div ref="menuRef" class="flex">
      <button
        class="w-[50px] h-[50px] ml-4 flex flex-col justify-evenly items-center cursor-pointer absolute left-0 top-[50%] -translate-y-[50%] md:hidden"
        @click.stop="toogleMenu()"
      >
        <span
          class="bg-[#f4f4f5] w-[90%] h-[2px] block transform transition-all duration-500"
          :class="stateMenu ? '' : 'origin-center rotate-45 translate-y-3'"
        ></span>
        <span
          class="bg-[#f4f4f5] w-[90%] h-[2px] block transform transition-all duration-500"
          :class="stateMenu ? '' : 'opacity-0'"
        ></span>
        <span
          class="bg-[#f4f4f5] w-[90%] h-[2px] block transform transition-all duration-500"
          :class="stateMenu ? '' : 'origin-center -rotate-45 -translate-y-3'"
        ></span>
      </button>
      <nav
        :class="
          stateMenu
            ? 'hidden md:flex md:flex-row'
            : 'w-screen max-h-max flex flex-col bg-[#1e293b] absolute left-0 top-[60px]'
        "
      >
        <ul class="md:flex md:gap-6 md:text-lg lg:text-2xl">
          <li
            @click="
              () => {
                stateMenu = true;
              }
            "
            class="w-[100%] h-[30px] grid place-items-center uppercase font-semibold tracking-[2px]"
          >
            <a href="#home">Inicio</a>
          </li>
          <li
            @click="
              () => {
                stateMenu = true;
              }
            "
            class="w-[100%] h-[30px] grid place-items-center uppercase font-semibold tracking-[2px]"
          >
            <a href="#habilidades">Habilidades</a>
          </li>
          <li
            @click="
              () => {
                stateMenu = true;
              }
            "
            class="w-[100%] h-[30px] grid place-items-center uppercase font-semibold tracking-[2px]"
          >
            <a href="#projetos">Projetos</a>
          </li>
        </ul>
      </nav>
    </div>
    <h1 class="md:text-xl md:tracking-[2px] lg:text-2xl">{{ nome }}</h1>
  </header>
</template>
