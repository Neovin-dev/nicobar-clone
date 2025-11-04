<template>
  <div class="cursor-pointer bg-white p-1 overflow-hidden transition-all duration-300 group" :style="{ flex: `0 0 ${productCardWidth}` }">
    <div class="relative w-full aspect-3/4 bg-gray-100 group">
        <span 
          class="absolute top-3 text-xs font-normal px-2 py-1 z-1"
          :style="{ 
            'background-color': productData.tags.includes('bestsellerproduct') ? '#1c1b1b' : 'white',
            'color': productData.tags.includes('bestsellerproduct') ? 'white': 'black'
            }"
        >
          {{ productData.tags.includes('bestsellerproduct')? 'BestSeller': 'New' }} 
        </span>
        <img 
            :key="currentImage.id" 
            :src="currentImage.src" 
            :alt="productData.title" 
            class="absolute top-0 left-0 w-full h-full object-cover"
        >
        <button 
        @click="nextImage(-1)" 
        class="absolute left-2 top-1/2 -translate-y-1/2 p-2 text-gray-800 opacity-0 group-hover:opacity-100 transition-opacity duration-100 focus:outline-none"
        >
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" /></svg>
        </button>
        <button 
          @click="nextImage(1)" 
          class="absolute right-2 top-1/2 -translate-y-1/2 p-2  text-gray-800 opacity-0 group-hover:opacity-100 transition-opacity duration-100 focus:outline-none"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" /></svg>
        </button>

    </div>

    <div v-if="widthCalc" class="w-full  flex flex-[100%] text-[#1c1c1b] bg-[#F3F7F7]">
      <div class="border-[#e0e2e4] border uppercase underline px-2.5 py-3 flex-[70%] text-[#1c1c1b] flex justify-center">
        Add to cart
      </div>
      <div class="px-2.5 py-3 flex border border-[#e0e2e4] flex-[30%] border-l-none">
        <button class="text-gray-500 mr-2 flex-[30%] flex justify-center h-full">
          <svg xmlns="http://www.w3.org/2000/svg" width="25" height="20" viewBox="0 0 21 15" fill="none">
            <path d="M9.29993 9.46275C10.155 8.54987 11.0454 7.5992 11.6389 6.76835L11.6411 6.76529L11.6415 6.7647L11.6437 6.76159L11.6438 6.76147C12.4473 5.65187 12.4321 4.25218 12.0603 3.35302C11.9028 2.97213 11.5139 2.28015 10.7221 2.15245C10.5559 2.12564 10.3965 2.11186 10.2482 2.11186C9.74977 2.11186 9.37539 2.26376 9.08808 2.59681C8.80113 2.92947 8.68345 3.34015 8.65411 3.45753L8.64884 3.47861L8.64285 3.49958C8.40578 4.32927 7.70406 4.87975 6.90191 4.87975C6.06746 4.87975 5.34965 4.29322 5.11482 3.40162L5.11485 3.40162L5.11414 3.39916C4.93177 2.77221 4.64269 2.44389 4.3438 2.27643C4.04991 2.11177 3.76127 2.11178 3.59979 2.11179H3.59682C3.44942 2.11179 3.29032 2.1256 3.11723 2.15349C2.35138 2.27328 1.95359 2.86411 1.75786 3.3194L1.75786 3.3194C1.29573 4.39437 1.44613 5.77968 2.12865 6.77659L2.12863 6.7766L2.12987 6.77834C2.71574 7.59607 3.60345 8.53295 4.45573 9.43243L4.45942 9.43632C5.32068 10.3453 6.15267 11.2235 6.81987 12.0939L6.89905 12.1972L6.97846 12.0941C7.63976 11.2353 8.45382 10.3661 9.29621 9.46672L9.29993 9.46275ZM7.48313 3.16822L7.48318 3.16824L7.48399 3.165C7.55847 2.86708 7.75126 2.29991 8.17473 1.80897C8.59536 1.32132 9.24576 0.905716 10.2483 0.905731C10.4545 0.905735 10.6762 0.92332 10.9142 0.961715C12.1713 1.16447 13.0334 2.17943 13.3641 3.46099C13.6948 4.74223 13.4876 6.27177 12.6207 7.46887L12.6203 7.4694C11.9808 8.36482 11.0856 9.32054 10.1801 10.2873C9.8979 10.5886 9.61471 10.891 9.33793 11.1929C8.75731 11.8263 8.20601 12.457 7.75719 13.0678C7.38321 13.5768 7.07745 14.0758 6.88563 14.5548C6.70838 14.0754 6.41041 13.5764 6.04026 13.0681C5.59515 12.4569 5.04096 11.8261 4.45502 11.1926C4.16782 10.8821 3.87329 10.5713 3.57991 10.2616C2.67222 9.30362 1.7756 8.35731 1.14174 7.47006C0.316035 6.27232 0.109034 4.74213 0.439651 3.46099C0.770176 2.18021 1.63173 1.16485 2.93127 0.961794L2.93176 0.961715C3.17047 0.923214 3.39146 0.905664 3.59682 0.905664C4.59188 0.905664 5.22111 1.31903 5.62261 1.7947C6.02633 2.27301 6.20242 2.81788 6.27804 3.08228C6.37331 3.46106 6.62609 3.67362 6.90192 3.67362C7.15939 3.67362 7.39202 3.48708 7.48313 3.16822Z" fill="#2D333D" stroke="white" stroke-width="0.2"></path>
            <path d="M17.4261 0.864465C16.653 0.682082 15.839 0.821673 15.1708 1.25121C14.5026 1.68074 14.0377 2.36335 13.8826 3.14239C13.7139 3.73296 13.039 3.73296 12.8702 3.05802C12.7149 2.30139 12.2588 1.64037 11.6065 1.22672C10.9542 0.813065 10.1618 0.682308 9.41116 0.864466C6.7114 1.2863 5.86772 5.08284 7.55508 7.5295C9.24243 9.89179 12.7859 12.6759 13.3764 14.8695C14.0514 12.6759 17.5104 9.89179 19.1978 7.5295C20.9695 5.08284 20.0415 1.2863 17.4261 0.864465Z" fill="#2D333D"></path>
            </svg>       
        </button>
      </div>
    </div>

    <div class="p-4">
        <div class="flex justify-between pb-2">
          <span class="inline-block border border-gray-300 text-[10px] font-medium px-2 py-0.5 mb-1">
              {{ productData.material[0] ? productData.material[0].toUpperCase(): '' }} 
          </span>
          <div v-if="!widthCalc" class="flex"> 
            <button class="text-gray-500 mr-2">
              <svg xmlns="http://www.w3.org/2000/svg" width="21" height="15" viewBox="0 0 21 15" fill="none">
                <path d="M9.29993 9.46275C10.155 8.54987 11.0454 7.5992 11.6389 6.76835L11.6411 6.76529L11.6415 6.7647L11.6437 6.76159L11.6438 6.76147C12.4473 5.65187 12.4321 4.25218 12.0603 3.35302C11.9028 2.97213 11.5139 2.28015 10.7221 2.15245C10.5559 2.12564 10.3965 2.11186 10.2482 2.11186C9.74977 2.11186 9.37539 2.26376 9.08808 2.59681C8.80113 2.92947 8.68345 3.34015 8.65411 3.45753L8.64884 3.47861L8.64285 3.49958C8.40578 4.32927 7.70406 4.87975 6.90191 4.87975C6.06746 4.87975 5.34965 4.29322 5.11482 3.40162L5.11485 3.40162L5.11414 3.39916C4.93177 2.77221 4.64269 2.44389 4.3438 2.27643C4.04991 2.11177 3.76127 2.11178 3.59979 2.11179H3.59682C3.44942 2.11179 3.29032 2.1256 3.11723 2.15349C2.35138 2.27328 1.95359 2.86411 1.75786 3.3194L1.75786 3.3194C1.29573 4.39437 1.44613 5.77968 2.12865 6.77659L2.12863 6.7766L2.12987 6.77834C2.71574 7.59607 3.60345 8.53295 4.45573 9.43243L4.45942 9.43632C5.32068 10.3453 6.15267 11.2235 6.81987 12.0939L6.89905 12.1972L6.97846 12.0941C7.63976 11.2353 8.45382 10.3661 9.29621 9.46672L9.29993 9.46275ZM7.48313 3.16822L7.48318 3.16824L7.48399 3.165C7.55847 2.86708 7.75126 2.29991 8.17473 1.80897C8.59536 1.32132 9.24576 0.905716 10.2483 0.905731C10.4545 0.905735 10.6762 0.92332 10.9142 0.961715C12.1713 1.16447 13.0334 2.17943 13.3641 3.46099C13.6948 4.74223 13.4876 6.27177 12.6207 7.46887L12.6203 7.4694C11.9808 8.36482 11.0856 9.32054 10.1801 10.2873C9.8979 10.5886 9.61471 10.891 9.33793 11.1929C8.75731 11.8263 8.20601 12.457 7.75719 13.0678C7.38321 13.5768 7.07745 14.0758 6.88563 14.5548C6.70838 14.0754 6.41041 13.5764 6.04026 13.0681C5.59515 12.4569 5.04096 11.8261 4.45502 11.1926C4.16782 10.8821 3.87329 10.5713 3.57991 10.2616C2.67222 9.30362 1.7756 8.35731 1.14174 7.47006C0.316035 6.27232 0.109034 4.74213 0.439651 3.46099C0.770176 2.18021 1.63173 1.16485 2.93127 0.961794L2.93176 0.961715C3.17047 0.923214 3.39146 0.905664 3.59682 0.905664C4.59188 0.905664 5.22111 1.31903 5.62261 1.7947C6.02633 2.27301 6.20242 2.81788 6.27804 3.08228C6.37331 3.46106 6.62609 3.67362 6.90192 3.67362C7.15939 3.67362 7.39202 3.48708 7.48313 3.16822Z" fill="#2D333D" stroke="white" stroke-width="0.2"></path>
                <path d="M17.4261 0.864465C16.653 0.682082 15.839 0.821673 15.1708 1.25121C14.5026 1.68074 14.0377 2.36335 13.8826 3.14239C13.7139 3.73296 13.039 3.73296 12.8702 3.05802C12.7149 2.30139 12.2588 1.64037 11.6065 1.22672C10.9542 0.813065 10.1618 0.682308 9.41116 0.864466C6.7114 1.2863 5.86772 5.08284 7.55508 7.5295C9.24243 9.89179 12.7859 12.6759 13.3764 14.8695C14.0514 12.6759 17.5104 9.89179 19.1978 7.5295C20.9695 5.08284 20.0415 1.2863 17.4261 0.864465Z" fill="#2D333D"></path>
                </svg>       
            </button>
          
          <button
           class="text-gray-500 mr-1.5">
            <svg class="xs-hide" width="19" height="18" viewBox="0 0 19 18" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect x="1.10938" y="5.93164" width="16.5913" height="10.9381" stroke="#2B2C2F" stroke-linecap="round" stroke-linejoin="round"></rect>
            <path d="M12.5753 4.17047C12.5753 2.41968 11.1549 1 9.40479 1C7.65326 1 6.23438 2.41968 6.23438 4.17047V5.93182H12.5753V4.17047Z" stroke="#2B2C2F" stroke-linecap="round" stroke-linejoin="round"></path>
            </svg>    
          </button>
        </div>
        </div>
      
      <div class="flex items-center justify-between mt-2 mb-3 relative w-full bg-white">
        <div class="flex items-center justify-between w-full mt-1 mb-3 absolute left-0 top-[-0.5] h-2 bg-white  py-2 group-hover:opacity-0 group-hover:invisible transition-opacity duration-300">
          <div class="flex space-x-2 text-[14px] pr-2 mt-2 bg-white items-center justify-center rounded-sm w-full">
            <span class="w-full"> {{ productData.title }}</span>
          </div>
        </div>
        <div class="flex space-x-2 text-[14px] mt-0">
          <button 
            v-for="size in getSizes" 
            :key="size"
            :class="[
              'pr-2 h- flex items-center justify-center rounded-sm',
            ]"
          >
            {{ size }}
          </button>
        </div>

      </div>
      
      <p class="text-[11px] text-gray-900">
        ₹ {{ formattedPrice }}
      </p>

      <div v-if="widthCalc" class="flex space-x-2 text-[14px] mt-0">
          <button 
            v-for="size in getSizes" 
            :key="size"
            :class="[
              'pr-2 h- flex items-center justify-center rounded-sm',
            ]"
          >
            {{ size }}
          </button>
      </div>

      <div class="flex space-x-2 mt-3">
        <button 
          v-if="getColors.length > 1"
          v-for="color in getColors" 
          :key="color"
          :style="{ backgroundColor: color }" 
          :class="['w-3.5 h-3.5 rounded-full border border-gray-300',]"
        ></button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ProductCard',
  props: {
    productData: {
      type: Object,
      required: true
    },
    productCardWidth: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      imageIndex: 0 as number,
      widthCalc: window.innerWidth < 1024,
    };
  },

  computed: {
    formattedPrice(): string {
      let formattedNumber = new Intl.NumberFormat('en-IN').format(this.productData.price);
      return formattedNumber; 
    },
    
    currentImage(): { id: number, src: string } {
      return this.productData.images[this.imageIndex] || {};
    },

    getSizes(): string[] {
      const sizeOption = this.productData.options.find((option: any) => option.name === 'Size');
      return sizeOption ? sizeOption.values : [];
    },

    getColors(): string[] {
      const colorOption = this.productData.options.find((option: any) => option.name === 'Color');
      return colorOption ? colorOption.values : [];
    }
  },
  
  methods: {
    nextImage(step: number) {
      const numImages = this.productData.images.length; 
      let newIndex = this.imageIndex + step;

      if (newIndex >= numImages) {
        newIndex = 0;
      } else if (newIndex < 0) {
        newIndex = numImages - 1;
      }
      
      this.imageIndex = newIndex; 
    }
  },
});
</script>