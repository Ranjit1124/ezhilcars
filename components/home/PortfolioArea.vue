<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, EffectFade, Autoplay } from "swiper/modules";
import "swiper/swiper-bundle.css";

import portfolio_img_1 from "~/assets/images/projects/work1.jpg";
import portfolio_img_2 from "~/assets/images/projects/work2.jpg";
import portfolio_img_3 from "~/assets/images/projects/work3.jpg";
import portfolio_img_4 from "~/assets/images/projects/work4.jpg";
import portfolio_img_5 from "~/assets/images/projects/work5.jpg";
import portfolio_img_6 from "~/assets/images/projects/work6.jpg";

const portfolio_data = [
  { id: 1, img: portfolio_img_1, category: "Premium", title: "BMW 530 D" },
  { id: 2, img: portfolio_img_2, category: "Hatchback", title: "Nissan Magnite" },
  { id: 3, img: portfolio_img_3, category: "Sedan", title: "Skoda Superb" },
  { id: 4, img: portfolio_img_4, category: "Hatchback", title: "VolksWagen GT" },
  { id: 5, img: portfolio_img_5, category: "Hatchback", title: "Maruthi Ignis" },
  { id: 6, img: portfolio_img_6, category: "Hatchback", title: "VolksWagen GT" },
];

const categories = [
  "All",
  ...new Set(portfolio_data.map((item) => item.category)),
];

const activeCategory = ref("All");
const items = ref(portfolio_data);

const filterItems = (cateItem) => {
  activeCategory.value = cateItem;
  items.value = cateItem === "All" ? portfolio_data : portfolio_data.filter((item) => item.category === cateItem);
};

const props = defineProps({
  cls: String,
});

import { ref } from "vue";
import ImagePopup from "~/components/common/Imagepopup.vue";
import "vue-easy-lightbox/external-css/vue-easy-lightbox.css";

const image_popup = ref(null);
function handleImagePopup(index) {
  image_popup.value.showImg(index);
}
</script>

<template>
  <div>
    <section id="portfolio" :class="`portfolio-area ${props.cls}`">
      <div class="container">
        <div class="container-inner">
          <div class="row">
            <div class="col-xl-12 col-lg-12">
              <div class="section-title text-center wow fadeInUp delay-0-2s">
                <h2>Available Cars</h2>
                <p>
                  Explore our latest pre-owned vehicles, carefully selected and restored with great attention to detail, each one showcasing the care and commitment we put into every car.
                </p>
              </div>
            </div>
          </div>
          <ul class="project-filter filter-btns-one justify-content-left pb-15 wow fadeInUp delay-0-2s">
            <li v-for="(item, i) in categories" :key="i">
              <a @click="filterItems(item)" :class="`${item === activeCategory ? 'current' : ''}`">
                <span>{{ item }}</span>
              </a>
            </li>
          </ul>
          <div class="row project-masonry-active">
            <Swiper
              :spaceBetween="30"
              :autoplay="{ delay: 1500, disableOnInteraction: false }"
              :modules="[Navigation, EffectFade, Autoplay]"
              :navigation="{ nextEl: '.testimonial-next', prevEl: '.testimonial-prev' }"
              :loop="true"
              :breakpoints="{
                320: { slidesPerView: 1 },  // Small screens
                992: { slidesPerView: 3 }   // Larger screens
              }"
              class="testimonials-wrap"
            >
              <SwiperSlide
                v-for="(item, i) in items"
                :key="i"
                class="col-lg-4 col-md-6 item branding game"
              >
                <div class="project-item style-two wow fadeInUp delay-0-3s">
                  <div class="project-image">
                    <img :src="item.img" alt="Project" class="responsive-img" />
                    <a style="cursor: pointer" @click.prevent="handleImagePopup(i)" class="details-btn">
                      <i class="ri-arrow-right-up-line"></i>
                    </a>
                  </div>
                  <div class="project-content">
                    <span class="sub-title">{{ item.category }}</span>
                    <h3>
                      <NuxtLink to="/single-project">{{ item.title }}</NuxtLink>
                    </h3>
                  </div>
                </div>
              </SwiperSlide>
            </Swiper>
            <div class="slider-arrows wow fadeInUp delay-0-6s text-center pt-40">
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
    </section>

    <!-- Image Popup -->
    <ImagePopup ref="image_popup" :images="portfolio_data.map((item) => item.img)" />
  </div>
</template>

<style scoped>
.responsive-img {
  width: fit-content; /* Default to full width */
  height: auto; /* Maintain aspect ratio */
}

/* For smaller screens */
@media (max-width: 600px) {
  .responsive-img {
    width: 400px;  /* Set width to 50px for smaller screens */
    height: 400px; /* Adjust height accordingly for smaller screens */
  }
}

/* For larger screens */
@media (min-width: 601px) {
  .responsive-img {
    width: 500px;  /* Set width to 50px for medium to large screens */
    height: 400px; /* Set height to 400px for medium to large screens */
  }
}
</style>
