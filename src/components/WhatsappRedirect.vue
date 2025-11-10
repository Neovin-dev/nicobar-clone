<template>
<div class="whatsapp-wrapper h-[50px] fixed z-10 w-[50px] right-[25px] bottom-[85px]">
    <div id="sy-whatshelp ">
        <a href="https://api.whatsapp.com/send?phone=919560663318&amp;text=Hi%20Nico%20folks.%20Could%20you%20please%20help%20me%20with%20something?" target="_blank" class="sywh-open-services " data-html="true" data-placement="left">
            <img src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/WA_without_Stroke.png?v=1757582541">
        </a> 
    </div>       
</div>
</template>

<script lang='ts'>
import { defineComponent } from "vue";


export default defineComponent({
    name: "WhatsappRedirect"
});
</script>

<style scoped>
@media (max-width: 468px){
   .whatsapp-wrapper {
    height: 30px;
    width: 30px;
    bottom: 95px;
    } 
} 

</style>