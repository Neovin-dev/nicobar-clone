<template>
<div class="search-bar-wrapper flex-[100%]">
    <div class="searchbar w-full relative flex-[80%] pr-20 border-b border-t flex">
        <input  @input="handleInput" ref="searchInput" type="text" class="search-input text-[21px] font-thin w-full min-w-[180px] bg-white bg-none bg-position-[20px] bg-no-repeat leading-[normal] text-[#22272f] pl-5 pr-[130px] py-[30px] placeholder:text-sm placeholder:font-bold overflow-hidden whitespace-nowrap text-ellipsis focus:outline-none" placeholder="Search for a Product, Category.. ">
        <span v-if="activeReset" @click="resetValues" class="cursor-pointer reset-container underline absolute right-20 top-0 h-full items-center flex text-[12px]">Reset</span>
        <svg @click="resetsPage" class="cross-svg  cursor-pointer h-8 w-8 absolute right-5 top-[30%]" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <path d="M19 5L5 19M5.00001 5L19 19" stroke="#000000" stroke-width="0.72" stroke-linecap="round" stroke-linejoin="round"></path> </g></svg>
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
    data(){
        return {
            activeReset: false as boolean,
        }
    },
    emits: ['update-search', 'close-search-bar'],
    methods: {
        handleInput(event: Event){
            const target = event.target as HTMLInputElement;
            
            if(target.value.length > 0){
                this.activeReset = true;
                this.$emit('update-search', target.value); 
                console.log("character entered", target.value)
            }else {
                this.activeReset = false;
                this.$emit('update-search', 'shirts mens'); 
                console.log("character entered", 'mens kurta')
            }
        },
        resetValues(){
            const inputElement = this.$refs.searchInput as HTMLInputElement;

            if (inputElement) {
                inputElement.value = ''; 
                this.$emit('update-search', 'mens kurta');
                this.activeReset = false; 
            }
            this.$emit('update-search', 'mens kurta');
            this.$emit('close-search-bar');
        },
        resetsPage(){
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
        },
    },
})
</script>

<style scoped>

@media (max-width: 820px){
    .search-input {
        /* margin: 20px; */
        padding: 10px;
        /* border: 0;
        border-bottom: 1px solid black; */
    }
    .searchbar {
        border-top: none;
    }
    .cross-svg {
        height: 20px;
        width: 20px;
    }

}
</style>