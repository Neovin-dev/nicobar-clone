<template>
<div @click="backToTopFn" v-if="visibility" class="back-to-top-wrapper fixed bottom-22.5 right-22.5 bg-white px-4 py-2 text-[12px] rounded-full shadow-[0_2px_4px_#00000029] cursor-pointer">
    <div class="product-count-backtotop flex">
        <!-- <span class="view-count"> -->
            <!-- Display how many cards passed behind me here -->
             <!-- {{ viewCount }} -->
        <!-- </span> -->
        <!-- <span>/</span> -->
        <total-product-count class="pr-2">
            {{ displayData.totalHits ? displayData.totalHits: 'No' }} Items
        </total-product-count>
        <img src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/arrow-top.svg?v=1671523432" alt="back to top"></img>
    </div>
</div>

</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: 'ProductCounter',
    props: {
        displayData: {
            type: Object,
            required: true,
        }
    },
    data() {
        return {
            visibility: true as boolean,
            viewCount: 0 as number,
        }
    },
    mounted(){
        window.addEventListener('scroll', this.visibilityBTT);
        this.visibilityBTT();
    },
    unmounted(){
        window.removeEventListener('scroll', this.visibilityBTT);
    },
    methods: {
        backToTopFn(){
            window.scrollTo({
                top: 0,
                left: 0,
                behavior: 'smooth',
            });
        },
        visibilityBTT(){
            const currentScollPosition = window.scrollY;
            if(currentScollPosition >= 500){
                this.visibility = true;
            }else {
                this.visibility = false;
            }
        }
    }

})
</script>