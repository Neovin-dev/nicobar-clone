<template>
<div class="Pagination flex justify-center mb-20 mt-7.5">
    <div class="Pagination-navbar text-[12px] py-4 border-b">
        <span class="Pagination__NavItem px-7 py-4 border-b-2 shadow-[0_-2px_#1c1b1b_inset] border-b-[#1c1b1b]">1</span>
        <span class="Pagination__NavItem px-7 py-4">2</span>
        <span class="Pagination__NavItem px-7 py-4">3</span>
        <span class="Pagination__NavItem px-7 py-4">4</span>
        <span class="Pagination__NavItem px-7 py-4">...</span>
        <span class="Pagination__NavItem px-7 py-4">></span>
    </div>
</div>

</template>


<script lang="ts">
import { defineComponent } from "vue";


export default defineComponent({
    name: 'PaginationSection',
})
</script>