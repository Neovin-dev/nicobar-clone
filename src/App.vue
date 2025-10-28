<script setup lang="ts">
import HeaderBar from './components/HeaderBar.vue';
import AnnouncementCarousel from './components/HeaderComponents/AnnouncementCarousel.vue';
import ProductCard from './components/ProductCard.vue';
import TopCarousel from './components/TopCarousel.vue';
</script>

<template>
  <AnnouncementCarousel />
  <HeaderBar />
  <section class="collection-banner-image w-full overflow-hidden no-scrollbar">
    <!-- for less than 1024 -->
      <!-- <img class="w-full overflow-hidden align-top max-h-[400px] object-cover object-center" fetchpriority="high" loading="eager" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/MW_BANNER_MOBILE_e3069101-3895-494d-91ac-09b90991392e.png?v=1757422516"> -->
       <!-- for more than 1024 -->
       <img class="w-full" fetchpriority="high" loading="eager" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/MW_BANNER_4b96e466-06ee-4ceb-9d54-7154dc694012.png?v=1757422514">
  </section>
  <TopCarousel />
  <div class="relative express-plp flex justify-between items-center w-[calc(100%-79px)] mt-auto mb-[15px] mx-auto border-y-[#dfe1e3] border-t border-solid border-b h-[50px] p-[5px] pl-2.5 pr-2.5">
      <span id="express-plp-pincode" class="text-[12px] text-center"><span>Express Delivery:</span> <u>PIN code</u></span>
      <span class="apply-filter flex text-[12px] text-[#bcbcbc]">
        <img class="absolute right-[130px] bottom-0 h-[37px] pointer-events-none" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/Export_this_1.png?v=1754475935" alt="icon">
        APPLY FILTER
      </span>
  </div>
  <ProductCard />
  <ProductCard />
  <ProductCard />
  <ProductCard />
  
</template>

<style scoped>
</style>
