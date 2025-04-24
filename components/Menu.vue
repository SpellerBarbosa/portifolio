<script setup lang="ts">
import { ref } from 'vue';

const stateMenu = ref<boolean>(true);
const menuRef = ref<HTMLElement | null>(null);

const toogleMenu = () => {
    stateMenu.value = !stateMenu.value;
}

const handerClickOutSide = (Event: MouseEvent) => {
    if (menuRef.value && !menuRef.value.contains(Event.target as Node)) {
        stateMenu.value = true;
    }
}

onMounted(() => {
    document.addEventListener('click', handerClickOutSide);
});

onUnmounted(() => {
    document.removeEventListener('click', handerClickOutSide);
});
</script>

<template>
    <header class=" flex justify-between text-[#F4F4F5] w-screen  items-center font-inter relative">
        <div  ref="menuRef" class="relative z-10">
            <button class="w-[50px] h-[50px] flex flex-col justify-evenly items-center" @click.stop="toogleMenu()">
            <span class="bg-[#f4f4f5] w-[90%] h-[2px] block transform transition-all duration-500"
                :class="stateMenu ? '' : 'origin-center rotate-45 translate-y-3'"></span>
            <span class="bg-[#f4f4f5] w-[90%] h-[2px] block transform transition-all duration-500"
                :class="stateMenu ? '' : 'opacity-0'"></span>
            <span class="bg-[#f4f4f5] w-[90%] h-[2px] block transform transition-all duration-500"
                :class="stateMenu ? '' : 'origin-center -rotate-45 -translate-y-3'"></span>
        </button>
        <nav class="w-screen absolute top-[55px]" :class="!stateMenu ? 'flex flex-col' : 'hidden'">
            <ul class="w-screen flex flex-col items-center bg-[#562478]">
                <li>Inicio</li>
                <li>Sobre</li>
                <li>Skills</li>
                <li>Projetos</li>
                <li>Contato</li>
            </ul>
        </nav>
        </div>
        <h1 class="text-3xl font-bold tracking-[10px] mr-[50%] translate-x-[50%]">F.B</h1>
    </header>
</template>