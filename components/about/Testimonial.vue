
<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, EffectFade, Autoplay } from "swiper/modules";


const achievement_data = [
  {
    id: 1,
    topic: "50+ Cars Sold",
    description: "Successfully matched over 50 happy customers with their perfect pre-owned cars in record time.",
  },
  {
    id: 2,
    topic: "100% Client Satisfaction",
    description: "Proud to maintain a perfect track record of customer satisfaction, reflecting our commitment to quality and transparency.",
  },
  {
    id: 3,
    topic: "Only Quality-Assured Cars",
    description: "Each vehicle in our inventory undergoes a rigorous multi-point inspection, ensuring only top-quality cars are available.",
  },
  {
    id: 4,
    topic: "Trusted by the Community",
    description: "Built a strong reputation as a reliable pre-owned car dealer trusted by local families, professionals, and businesses.",
  },
  {
    id: 5,
    topic: "Expert Team with Industry Experience",
    description: "Our team combines years of expertise in car selection, evaluation, and customer service to deliver the best buying and selling experience.",
  },
  {
    id: 6,
    topic: "Fair and Transparent Pricing",
    description: "Consistently offering competitive and transparent pricing, making premium pre-owned cars accessible to everyone.",
  },
  {
    id: 7,
    topic: "5-Star Reviews Across Platforms",
    description:'Earned glowing reviews from satisfied customers on Google, Yelp, and other review platforms.'
  },
  {
    id: 8,
    topic: "Diverse Inventory",
    description:'Maintained a wide selection of vehicles to suit every budget and lifestyle, from economy cars to premium models.'

  },
  {
    id: 9,
    topic: "Fast Turnaround for Sellers",
    description:'Helped car owners sell their vehicles quickly and at the best market value, minimizing delays and maximizing satisfaction.'

  },
  {
    id: 10,
    topic: "Seamless Buying Experience",
    description:'Delivered a hassle-free, end-to-end buying and selling process with personalized assistance at every step.'

  },
];
</script> 


<template>
  <section class="testimonials-area">
    <div class="container">
      <div class="container-inner">
        <div class="row">
          <div class="col-xl-12 col-lg-12">
            <div class="section-title text-center wow fadeInUp delay-0-2s">
              <p>Testinomials</p>
              <h2>Achievements !</h2>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-lg-12">
            <Swiper
              :spaceBetween="30"
              :autoplay="{
                delay: 1500,
                disableOnInteraction: false,
              }"
              :modules="[Navigation, EffectFade, Autoplay]"
  :navigation="{
    nextEl: '.testimonial-next',
    prevEl: '.testimonial-prev',
  }"
  :loop="true" 
  :breakpoints="{
    320: { slidesPerView: 1 },  // For small screens (320px and up)
    992: { slidesPerView: 2 }   // For larger screens (992px and up)
  }"

  class="testimonials-wrap"
            >
            <template v-for="item in achievement_data" :key="item.id">
      <SwiperSlide class="testimonial-item wow fadeInUp delay-0-3s">
        <div class="testi-des">
          <h5>{{ item.topic }}</h5>
        </div>
        <div class="text">
          {{ item.description }}
        </div>
      </SwiperSlide>
    </template>
            
                        </Swiper>
            <div
              class="slider-arrows wow fadeInUp delay-0-6s text-center pt-40"
            >
              <button class="testimonial-prev arrow">
                <i class="ri-arrow-left-s-line"></i>
              </button>
              <button class="testimonial-next arrow">
                <i class="ri-arrow-right-s-line"></i>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

 