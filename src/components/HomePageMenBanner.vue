<template>
    <section class="collection-banner-image w-full overflow-hidden no-scrollbar">
    <!-- for less than 1024 -->
      <img v-if="widthCalculator" class="w-full overflow-hidden align-top max-h-[400px] object-cover object-center" fetchpriority="high" loading="eager" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/MW_BANNER_MOBILE_e3069101-3895-494d-91ac-09b90991392e.png?v=1757422516">
       <!-- for more than 1024 -->
       <img v-else class="w-full" fetchpriority="high" loading="eager" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/MW_BANNER_4b96e466-06ee-4ceb-9d54-7154dc694012.png?v=1757422514">
  </section>
    <div class="image-wrapper flex justify-center w-full overflow-x-auto mb-10">
    <div class="items flex w-full justify-center">
      <a 
        v-for="item in carouselItems" 
        :name="item.name" 
        :href="item.link" 
        class="flex flex-col items-center text-center no-underline text-gray-800"
      >
        <div class="image-container w-[90px] h-[90px] mt-10 ml-1 rounded-full overflow-hidden border flex border-none items-center justify-center">
          <img 
            fetchpriority="high" 
            class="object-cover w-full h-full" 
            :src="item.imageSrc" 
            :alt="item.name"
          >
        </div>
        
        <span class="image-text mt-2 text-[13px] font-medium whitespace-normal">
          {{ item.name }}
        </span> 
      </a>
    </div>
  </div>
  <div v-if="bannerEnable" class="relative express-plp flex justify-between items-center w-[calc(100%-79px)] mt-auto mb-[15px] mx-auto border-y-[#dfe1e3] border-t border-solid border-b h-[50px] p-[5px] pl-2.5 pr-2.5">
      <span id="express-plp-pincode" class="text-[12px] text-center"><span>Express Delivery:</span> <u>PIN code</u></span>
      <span class="apply-filter flex text-[12px] text-[#bcbcbc] fill-[#bcbcbc] cursor-pointer underline" @click="filterState">
        <img class="airplane-img absolute right-[90px] bottom-0 h-[37px] pointer-events-none" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/Export_this_1.png?v=1754475935" alt="icon">
        APPLY FILTER
      </span>
  </div>
  <div class="mens-collection-banner flex flex-col justify-center align-middle text-[#424954] text-center text-[15px] italic font-normal leading-5 tracking-[0.45px] w-[79%] m-auto py-3.5">
    <h1 class="title-express text-[#282b30] text-center text-xs not-italic flex justify-center font-bold pb-[15px] tracking-[1.2px] uppercase">All Men</h1>
    Check express delivery availability by PIN code and apply filter to browse.
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent ({
    name: 'HomePageMenBanner',
    emits: ['filter-state'],
    data() {
      return {
        carouselItems: [
          { name: 'Shirts', link: '#', imageSrc: 'https://www.nicobar.com/cdn/shop/files/Shirts_d896521a-1c4b-4651-89bb-2e687f0d4623_180x.png?v=1757479108' },
          { name: 'Kurtas & Jackets', link: '#', imageSrc: 'https://www.nicobar.com/cdn/shop/files/Kurtas_c6db3f2e-105a-4953-80e0-9e57e0ac45b0_180x.png?v=1757479109' },
          { name: 'T-Shirts', link: '#', imageSrc: 'https://www.nicobar.com/cdn/shop/files/T-Shirts_Essentials_180x.png?v=1752822232' },
          { name: 'Trousers', link: '#', imageSrc: 'https://www.nicobar.com/cdn/shop/files/Trousers_522f8d82-de78-44b9-a908-551781502b45_180x.png?v=1757479108' },
          { name: 'Gifts for him', link: '#', imageSrc: 'https://www.nicobar.com/cdn/shop/files/GIFTS_FOR_HIM_747dd0d6-73d7-46eb-84c7-3a08509890d0_180x.png?v=1757479108' },
          { name: 'New Arrivals', link: '#', imageSrc: 'https://www.nicobar.com/cdn/shop/files/New_Arrivals_681b745c-d7a1-42a2-9879-6e42a79a3011_180x.png?v=1757479108' }, 
          { name: 'Bestsellers', link: '#', imageSrc: 'https://www.nicobar.com/cdn/shop/files/Bestsellers_3aa4dfad-cab3-4bad-9289-6f458e72e105_180x.png?v=1757479108' },
        ],
        widthCalculator: false as boolean,
        bannerEnable: true,
      };
    },
    methods: {
          filterState(){
            this.$emit('filter-state')
          },
        },
    mounted(){
      const windowInnerWidth = window.innerWidth;
      if(windowInnerWidth > 1024){
        this.widthCalculator = false;
      } else {
        this.widthCalculator = true;
      }
    }    
})
</script>

<style scoped>
.image-wrapper::-webkit-scrollbar {
  display: none;
}
.image-wrapper {
  scrollbar-width: none;
}
.image-wrapper {
  -ms-overflow-style: none;
}
.image-container {
    margin-right: 10px;

}
#express-plp-pincode {
  letter-spacing: .40px;
  font-size: 13px;
}

@media (max-width: 1024px){
  .image-container {
    height: 80px;
    width: 77px;
  }

  .title-express{
    font-size: 18px;
  }

  .express-plp {
    width: 100%;
    margin: inherit 0px;
  }
}

@media (max-width: 480px){
  .image-text {
    font-size: 11px;
  }
  .image-wrapper {
    padding: 0 2.5px;
  }

  .items {
    justify-content: flex-start;
  }

  .airplane-img {
    height: 25px;
  }
}
</style>