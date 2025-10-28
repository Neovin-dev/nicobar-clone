<script setup lang="ts">
import HeaderBar from './components/HeaderBar.vue';
import AnnouncementCarousel from './components/HeaderComponents/AnnouncementCarousel.vue';
import ProductCard from './components/ProductCard.vue';
import TopCarousel from './components/TopCarousel.vue';
</script>

<template>
  <AnnouncementCarousel />
  <HeaderBar />
  <section class="collection-banner-image w-full overflow-hidden no-scrollbar">
    <!-- for less than 1024 -->
      <!-- <img class="w-full overflow-hidden align-top max-h-[400px] object-cover object-center" fetchpriority="high" loading="eager" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/MW_BANNER_MOBILE_e3069101-3895-494d-91ac-09b90991392e.png?v=1757422516"> -->
       <!-- for more than 1024 -->
       <img class="w-full" fetchpriority="high" loading="eager" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/MW_BANNER_4b96e466-06ee-4ceb-9d54-7154dc694012.png?v=1757422514">
  </section>
  <TopCarousel />
  <div class="relative express-plp flex justify-between items-center w-[calc(100%-79px)] mt-auto mb-[15px] mx-auto border-y-[#dfe1e3] border-t border-solid border-b h-[50px] p-[5px] pl-2.5 pr-2.5">
      <span id="express-plp-pincode" class="text-[12px] text-center"><span>Express Delivery:</span> <u>PIN code</u></span>
      <span class="apply-filter flex text-[12px] text-[#bcbcbc] fill-[#bcbcbc]">
        <img class="absolute right-[130px] bottom-0 h-[37px] pointer-events-none" src="https://cdn.shopify.com/s/files/1/0270/5129/4854/files/Export_this_1.png?v=1754475935" alt="icon">
        APPLY FILTER
      </span>
  </div>

  <div class="mens-collection-banner flex flex-col justify-center align-middle text-[#424954] text-center text-[15px] italic font-normal leading-5 tracking-[0.45px] w-[79%] m-auto py-3.5">
    <h1 class="text-[#282b30] text-center text-xs not-italic flex justify-center font-bold pb-[15px] tracking-[1.2px] uppercase">All Men</h1>
    Check express delivery availability by PIN code and apply filter to browse.
  </div>

  <div class="collectionToolbar my-0.5 mx-10 flex justify-between">
    <div class="collectionToobarView flex flex-row py-5">
        <button aria-label="Show four products per row" class="CollectionToolbar__LayoutType is-active h-5 w-5 flex justify-center align-middle" data-action="change-layout-mode" data-grid-type="desktop" data-count="4" fdprocessedid="b0xfnh"><svg class="Icon Icon--wall-2" role="presentation">
        <g id="grid4" transform="translate(-73 -520)">
          <rect id="Rectangle_283" data-name="Rectangle 283" width="6" height="6" transform="translate(73 520)" fill="#1c1b1b"></rect>
          <rect id="Rectangle_284" data-name="Rectangle 284" width="6" height="6" transform="translate(82 520)" fill="#1c1b1b"></rect>
          <rect id="Rectangle_285" data-name="Rectangle 285" width="6" height="6" transform="translate(82 529)" fill="#1c1b1b"></rect>
          <rect id="Rectangle_286" data-name="Rectangle 286" width="6" height="6" transform="translate(73 529)" fill="#1c1b1b"></rect>
        </g>
      </svg></button>

      <button aria-label="Show two products per row" class="CollectionToolbar__LayoutType h-5 w-5 flex justify-center align-middle" data-action="change-layout-mode" data-grid-type="desktop" data-count="2" fdprocessedid="vbsbq8"><svg class="Icon Icon--wall-4 h-5 w-5" role="presentation">
        <g xmlns="http://www.w3.org/2000/svg" id="grid2" transform="translate(-73 -520)">
          <rect id="Rectangle_283" data-name="Rectangle 283" width="6" height="15" transform="translate(73 520)" fill="#bcbcbc"></rect>
          <rect id="Rectangle_284" data-name="Rectangle 284" width="6" height="15" transform="translate(82 520)" fill="#bcbcbc"></rect>
        </g>
      </svg></button>
      <span class="productCount text-[12px] text-[#9ea5ad] pl-2">
        371 Items
      </span>
    </div>
    <div class="collectionToolbarFilterSort flex h-10 align-middle">
      <div class="collectionToolbarSort inline-flex py-2 px-4 border-2 border-solid border-[#dfe1e3] rounded-full justify-center items-center">
        <div class="sort-by-select-header flex text-center text-[10px]">
        <span class="title-text text-[#9ea5ad]">
          Sort by:
        </span>
        <span class="active-sort-by flex items-center pl-1 font-bold">
          <span>Featured</span>
        </span>
        <div class="chevron-down-icon pl-2 pt-1.5">
          <svg aria-hidden="true" focusable="false" role="presentation" class="icon icon--wide h-1 w-2 "><path xmlns="http://www.w3.org/2000/svg" id="down-arrow" d="M990.5,3700.5l3-3,3,3" transform="translate(997.208 3701.207) rotate(180)" fill="none" stroke="#424a54" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></path></svg>
        </div>
        </div>
      <!-- <ul class="sort-by-data" style="top: 40px !important">
          <li value="created-descending" class="data first-child" data-index="3" data-value="created-descending"><span>What’s New</span></li>
          <li value="manual" class="data is-selected" data-index="0" data-value="manual"><span>Featured</span></li>
          <li value="price-ascending" class="data" data-index="1" data-value="price-ascending"><span>Price - low to high</span></li>
          <li value="price-descending" class="data" data-index="2" data-value="price-descending"><span>Price - high to low</span></li>
        </ul> -->
      </div>
      <div class="filter-container flex ml-2.5">
        <button class="filter-bar inline-flex py-2 px-6 border-2 border-solid border-[#dfe1e3] rounded-full justify-center items-center text-[10px]">
        <svg class="h-3 w-3 mr-2" xmlns="http://www.w3.org/2000/svg" width="13" height="12.294" viewBox="0 0 13 12.294">
          <g id="filters" transform="translate(0.5 0.5)">
            <g id="Group_1435" data-name="Group 1435">
            <circle id="Ellipse_24" data-name="Ellipse 24" cx="1.445" cy="1.445" r="1.445" transform="translate(4.541)" fill="none" stroke="#424a54" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></circle>
            <line id="Line_3" data-name="Line 3" x2="4.712" transform="translate(7.288 1.445)" fill="none" stroke="#424a54" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></line>
            <line id="Line_4" data-name="Line 4" x2="4.679" transform="translate(0 1.445)" fill="none" stroke="#424a54" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></line>
            <circle id="Ellipse_25" data-name="Ellipse 25" cx="1.445" cy="1.445" r="1.445" transform="translate(1.791 4.202)" fill="none" stroke="#424a54" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></circle>
            <line id="Line_5" data-name="Line 5" x2="7.603" transform="translate(4.397 5.647)" fill="none" stroke="#424a54" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></line>
            <line id="Line_6" data-name="Line 6" x2="1.789" transform="translate(0 5.647)" fill="none" stroke="#424a54" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></line>
            <circle id="Ellipse_26" data-name="Ellipse 26" cx="1.445" cy="1.445" r="1.445" transform="translate(3.139 8.405)" fill="none" stroke="#424a54" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></circle>
            <line id="Line_7" data-name="Line 7" x2="6.158" transform="translate(5.842 9.849)" fill="none" stroke="#424a54" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></line>
            <line id="Line_8" data-name="Line 8" x2="3.236" transform="translate(0 9.849)" fill="none" stroke="#424a54" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></line>
            </g>
          </g>
          </svg>
          FILTERS
        </button>
      </div>
      
    </div>
  </div>

  <div class="card-container flex flex-[100%] flex-wrap">
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
    <ProductCard />
  </div>
  
  
</template>

<style scoped>
</style>