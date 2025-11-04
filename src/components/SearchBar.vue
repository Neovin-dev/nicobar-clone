<template>
<div class="search-bar-wrapper">
    <div class="searchbar w-full relative">
        <input @keyup.enter="handleSearch" ref="searchInput" type="text" class="text-[21px] font-thin border w-full min-w-[180px] bg-white bg-none bg-position-[20px] bg-no-repeat leading-[normal] text-[#22272f] pl-5 pr-[130px] py-[30px] border-solid border-black placeholder:text-sm placeholder:font-bold" placeholder="Search for a Product, Category.. ">
        <span @click="handleSearch" class="absolute right-20 top-[30%] border p-1.5 flex items-center"><button class="cursor-pointer">Search</button></span>
        <span class="reset-container underline absolute right-20 top-0 h-full items-center hidden">reset</span>
        <span class="close-btn absolute right-5 top-0 items-center flex h-full" @click="$emit('close-search-bar')">
            <img src="../../public/cross-svgrepo-com.svg" class="h-3 w-3" alt="">
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
        // handleInput(event: Event){
        //     const target = event.target as HTMLInputElement;
        //     this.$emit('update-search', target.value);
        //     console.log("character entered", target.value)
        // },
        handleSearch(){
            const searchValue = (this.$refs.searchInput as HTMLInputElement)?.value || '';
            this.$emit('update-search', searchValue);
            console.log("Search query:", searchValue);
        }
    }
})
</script>