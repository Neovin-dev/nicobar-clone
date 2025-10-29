<template>
<div class="search-bar-wrapper">
    <div class="searchbar w-full relative">
        <input type="text" class="text-[14px] font-bold border w-full min-w-[180px] bg-white bg-none bg-position-[20px] bg-no-repeat leading-[normal] text-[#22272f] pl-5 pr-[130px] py-[30px] border-solid border-black" placeholder="Search for a Product, Category.. ">
        <span class="reset-container underline absolute right-20 top-[30%] hidden">reset</span>
        <span class="close-btn absolute right-0 top-0">
            <svg fill="#000000" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg" class="height-10">
                <g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <path d="M0 14.545L1.455 16 8 9.455 14.545 16 16 14.545 9.455 8 16 1.455 14.545 0 8 6.545 1.455 0 0 1.455 6.545 8z" fill-rule="evenodd"></path> </g>
            </svg>
        </span>
    </div>
</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: 'SearchBar',
})
</script>