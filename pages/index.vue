<script setup lang="ts">
useHead({
  htmlAttrs: {
    lang: 'pt-BR'
  },
  title: "Fernando Barbosa - Portfólio de Desenvolvedor", 
  meta: [
    // Descrição do site
    { name: "description", content: "Portfólio de Fernando Barbosa, desenvolvedor de software, apresentando projetos pessoais e profissionais nas áreas de Front-End, Back-End e Full-Stack." },

    // Palavras-chave relevantes
    { name: "keywords", content: "Fernando Barbosa, portfólio, desenvolvedor web, projetos pessoais, front-end, back-end, full-stack, programador" },

    // Autor da página
    { name: "author", content: "Fernando Barbosa" },

    // SEO para dispositivos móveis
    { name: "viewport", content: "width=device-width, initial-scale=1.0" },

    // Melhor para redes sociais (Open Graph - usado por Facebook, LinkedIn, etc.)
    { property: "og:title", content: "Fernando Barbosa - Portfólio de Desenvolvedor" },
    { property: "og:description", content: "Conheça os projetos de Fernando Barbosa, desenvolvedor focado em soluções criativas e eficientes para web." },
    { property: "og:type", content: "website" },
    { property: "og:url", content: "https://seusite.com.br" }, // troque para a URL real


    // Twitter Card
    { name: "twitter:card", content: "summary_large_image" },
    { name: "twitter:title", content: "Fernando Barbosa - Portfólio" },
    { name: "twitter:description", content: "Veja meus projetos e habilidades como desenvolvedor web." },
    { name: "twitter:image", content: "https://seusite.com.br/imagem-de-capa.jpg" }
  ],
  link: [
    // Favicon (ícone do site)
    { rel: "icon", href: "/favicon.ico" }
  ]
})


</script>


<template>
    <main class="bg-[#13171d] w-screen h-auto flex flex-col items-center">
        <Menu />
        <Introduction />
        <Skills />
        <Projects />
        <Footer />
    </main>
</template>