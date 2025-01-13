<script setup>
import Footer from "~/layouts/Footer.vue";
import Header from "~/layouts/Header.vue";
useHead({
  title: "Contact Ezhil cars",
});

onMounted(async () => {
  const wow = await import(/* @vite-ignore */'wow.js'); // Suppress Vite warning
  new wow.default().init();
});


</script>

<template>
  <div>
    <CommonScrollTop />
    <Header />
    <Contact />    
    <Footer />
  </div>
</template>
