

<script setup>
import Footer from "~/layouts/Footer.vue";
import Header from "~/layouts/Header.vue";
useHead({
  title: "Work Ezhil cars",
});

onMounted(async () => {
  const wow = await import(/* @vite-ignore */ 'wow.js'); // Suppress Vite warning
  new wow.default().init();
});

</script>


<template>
  <div>
    <CommonScrollTop />
    <Header />
    <HomePortfolioArea cls="innerpage-single-area" />  
    <HomeCtaArea />
    <Footer />
  </div>
</template>

 