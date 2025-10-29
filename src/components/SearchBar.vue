<template>
<div class="search-bar-wrapper">
    <div class="searchbar w-full relative">
        <input type="text" class="text-[14px] font-bold border w-full min-w-[180px] bg-white bg-none bg-position-[20px] bg-no-repeat leading-[normal] text-[#22272f] pl-5 pr-[130px] py-[30px] border-solid border-black" placeholder="Search for a Product, Category.. ">
        <span class="reset-container underline absolute right-20 top-[30%] hidden">reset</span>
        <span class="close-btn absolute right-5 top-1/3" @click="$emit('close-search-bar')">
            <img src="../../public/cross-svgrepo-com.svg" class="h-6 w-6" alt="">
        </span>
    </div>
</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: 'SearchBar',
    emits: ['update-search', 'close-search-bar'],
    methods: {
        handleInput(event: Event){
            const target = event.target as HTMLInputElement;
            this.$emit('update-search', target.value);
        },
    }
})
</script>