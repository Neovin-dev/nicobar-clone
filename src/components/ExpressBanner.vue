<template>
    <div class="relative express-plp flex justify-between items-center w-[calc(100%-79px)] mt-auto mb-[15px] mx-auto border-y-[#dfe1e3] border-t border-solid border-b h-[50px] p-[5px] pl-2.5 pr-2.5">
      <span id="express-plp-pincode" class="text-[12px] text-center"><span>Express Delivery:</span> <u>PIN code</u></span>
      <span class="apply-filter flex text-[12px] text-[#bcbcbc] fill-[#bcbcbc]">
        <img class="absolute right-[130px] bottom-0 h-[37px] pointer-events-none" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/Export_this_1.png?v=1754475935" alt="icon">
        APPLY FILTER
      </span>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";


export default defineComponent ({
    name: 'ExpressBanner',
})
</script>