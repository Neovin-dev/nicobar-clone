<template>
  <div class="flex justify-center w-full overflow-x-auto mb-10">
    <div class="flex md:space-x-5">
      <a 
        v-for="item in carouselItems" 
        :name="item.name" 
        :href="item.link" 
        class="flex flex-col items-center text-center no-underline text-gray-800"
      >
        <div class="w-[90px] h-[90px] mt-10 rounded-full overflow-hidden border flex border-none items-center justify-center ">
          <img 
            fetchpriority="high" 
            class="object-cover w-full h-full" 
            :src="item.imageSrc" 
            :alt="item.name"
          >
        </div>
        
        <span class="mt-2 text-[13px] font-medium whitespace-normal">
          {{ item.name }}
        </span> 
      </a>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent ({
  name: 'TopCarousel',
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
    };
  },
})
</script>