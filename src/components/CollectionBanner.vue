<template>
    <section class="collection-banner-image w-full overflow-hidden no-scrollbar">
    <!-- for less than 1024 -->
      <!-- <img class="w-full overflow-hidden align-top max-h-[400px] object-cover object-center" fetchpriority="high" loading="eager" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/MW_BANNER_MOBILE_e3069101-3895-494d-91ac-09b90991392e.png?v=1757422516"> -->
       <!-- for more than 1024 -->
       <img class="w-full" fetchpriority="high" loading="eager" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/MW_BANNER_4b96e466-06ee-4ceb-9d54-7154dc694012.png?v=1757422514">
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent ({
    name: 'CollectionBanner',
})
</script>