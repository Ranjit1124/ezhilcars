

<script setup>
import Footer from "~/layouts/Footer.vue";
import Header from "~/layouts/Header.vue";
useHead({
  title: "Service Ezhil cars",
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
    <ServiceArea />
    <!-- <ServicePricingArea />      -->
    <HomeCtaArea />
    <Footer />
  </div>
</template>

 