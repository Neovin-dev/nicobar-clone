<template>
<div class="search-bar-wrapper">
    <div class="searchbar w-full relative">
        <input  @input="handleInput" ref="searchInput" type="text" class="search-input text-[21px] font-thin border w-full min-w-[180px] bg-white bg-none bg-position-[20px] bg-no-repeat leading-[normal] text-[#22272f] pl-5 pr-[130px] py-[30px] border-solid border-black placeholder:text-sm placeholder:font-bold" placeholder="Search for a Product, Category.. ">
        <!-- <span class="absolute right-20 top-[30%] border p-1.5 flex items-center"><button class="cursor-pointer">Search</button></span> -->
        <span @click="resetValues" class="reset-container underline absolute right-20 top-0 h-full items-center flex">reset</span>
        <span class="close-btn absolute right-5 top-0 items-center flex h-full" @click="$emit('close-search-bar')">
            <img src="../../public/cross-svgrepo-com.svg" class="h-3 w-3" alt="">
        </span>
    </div>
</div>
</template>

<script lang="ts">
import { defineComponent, nextTick } from "vue";

export default defineComponent({
    name: 'SearchBar',
    props: {
        activeSearch: {
            type: Boolean,
            required: true,
        }
    },
    emits: ['update-search', 'close-search-bar'],
    methods: {
        handleInput(event: Event){
            const target = event.target as HTMLInputElement;
            this.$emit('update-search', target.value);
            console.log("character entered", target.value)
        },
        resetValues(){
            this.$emit('update-search', 'mens kurta');
            this.$emit('close-search-bar');
        },
        focusInput() {
            const inputElement = this.$refs.searchInput as HTMLInputElement;
            if (inputElement) {
                inputElement.focus();
            }
        },

    },
    watch: {
        activeSearch: {
            immediate: true,
            handler(newValue: boolean) {
                if (newValue) {
                    nextTick(() => {
                       this.focusInput(); 
                    })
                }
            }
        }
    },
})
</script>

<style scoped>

@media (max-width: 820px){
.search-input {
    margin: 20px;
    padding: 10px;
    border: 0;
    border-bottom: 1px solid black;
}
}
</style>