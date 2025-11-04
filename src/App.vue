<template>
  <AnnouncementCarousel />
  <HeaderBar 
      @enable-search-bar="enableSearchBar"
  />
  <SearchBar 
      v-if="isSearchEnable" 
      @close-search-bar="closeSearchBar"
      @update-search="searchOperation"
  />
  <div v-else>
      <HomePageMenBanner @filter-state="toggleVisibility"/>
  </div>

  <CollectionToolbar
          @handle-sort="selectedSortOp"
          @filter-state="toggleVisibility"
          :sort-visible="isSortVisible" 
          @sort-state="toggleSortState"
          :display-data="searchResult"
          @grid-changer="updateProductCardWidth"
          :filter-tags="filterObject"
          @remove-filter-tag="handleRemoveTag"           @clear-all-filter-tags="handleClearAllTags"
  />

  <div class="card-container flex flex-[100%] flex-wrap">

  <div v-if="isLoading" class="loading-overlay w-full flex items-center justify-center h-50" >
    <span class="w-full flex items-center justify-center ">
      <img class="animate-spin w-20 h-20" src="./assets/image.png" alt="">
    </span>
    <!-- <span>Loading Products...</span> -->
  </div>
    
    <ProductCard 
        v-else-if="!isLoading"
        v-for="product in searchResult.results" 
        :key="product.id"
        :product-data="product"
        :product-card-width="productCardWidth"
    />

    <div class="no-results w-full" v-if="searchResult.totalHits === 0">
      <div class="container flex-col items-center flex justify-center">
        <div class="no-result-img flex flex-col w-100 justify-center items-center"><img src="../public/image.png" alt=""></div> 
        <h2 class="page-heading flex flex-col w-100 justify-center items-center">Sorry, we can’t find any result <span>for "{{ searchValue }}"</span></h2> 
        <div class="search-pform flex flex-col w-100 justify-center items-center">
          <p> Please try a different term. 
            <span style="display: none;">or try <a class="highlight-text">clearing</a> some filters</span>
          </p>
        </div>
      </div> 
    </div>
  </div>
  
  <div class="pagination-wrapper w-full flex justify-center mb-20 mt-7.5">
      <paginate
        class="flex items-center gap-3 text-[#6A6A6A] my-5"
        :page-count= "Math.ceil(searchResult.totalHits/40)"
        :click-handler="paginationHandler"
        :prev-text="'<'"
        :next-text="'>'"
        :container-class="'pagination-element'"
        :page-class="'page-item'"
      ></paginate>
  </div>
    
  <!-- <SectionFooter /> -->

  <div>
    <transition name="slide-right">
    <ProductFilterSidebar 
        v-if="isFilterSidebar"
        @close-filter-bar="toggleVisibility" 
        :filter-data="searchFilter"
        @search-filters-active="updateActiveFilters"
    />
    </transition>
    <!-- @search-filters-active="editFilters" -->
  </div>
  
    <div v-if="isSortMobile" class="overlay w-full h-full bg-[#00000080] fixed top-0 bottom-0 z-10"></div>
    <div class="collectionToolbarFilterSort h-15 align-middle fixed bottom-0 w-full bg-white flex-[100%] py-2 px-5 z-20 hidden">
      <div class="collectionToolbarSort inline-flex py-2 px-6 border-2 mx-3 border-solid font-bold border-[#dfe1e3] rounded-full justify-center items-center relative cursor-pointer hover:bg-[#ebedf1] flex-[50%]">
          <div class="sort-by-select-header flex text-center text-[10px]">
              <span class="title-text text-[#1A1F29] uppercase">
                Sort by
              </span>
          </div>
        </div>
        <ul v-if="isSortMobile" class="flex flex-col sort-by-data absolute bottom-15 left-0 bg-white text-left text-[10px] text-[#1a1f29] z-10 w-full float-left shadow-[1px_1px_4px_#7070704d] m-0 cursor-pointer">
                <li value="title" class="data first-child tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid uppercase" data-index="3" data-value="title"><span>Sort By</span></li>
                <li value="created-descending" class="data first-child tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="3" data-value="created-descending"
                ><span>Featured</span></li>
                <li  value="whatsnew" class="data is-selected tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="0" data-value="whatsnew"
                ><span>What's New</span></li>
                <li  value="lowestPrice" class="data tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="1" data-value="lowestPrice"><span>Lowest Price</span></li>
                <li  value="highestPrice" class="data tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="2" data-value="highestPrice"><span>Highest Price</span></li>
        </ul>
      <div class="filter-container flex mx-3 flex-[50%]" >
          <button class="filter-bar inline-flex py-2 px-6 border-2 border-solid border-[#dfe1e3] font-bold rounded-full justify-center items-center  text-[10px] hover:bg-[#ebedf1] w-full cursor-pointer">
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
  
  <ProductCounter 
      :display-data="searchResult" 
  />
  <WhatsappRedirect />
</template>

<script lang="ts">

// Imports
import SearchClient from "@gaspl/search-client";

import Paginate from "vuejs-paginate-next";
import { defineComponent } from "vue";

// Working NICOBAR TOKENS
const searchToken = import.meta.env.VITE_NICOBAR_SEARCH_TOKEN as string;
const applicationId = import.meta.env.VITE_NICOBAR_APPLICATION_ID as string;
const collectionId = import.meta.env.VITE_NICOBAR_COLLECTION_ID as string;

// Client initialization
var searchClient = new SearchClient(applicationId, searchToken);

// Componenet Imports
import HeaderBar from './components/HeaderBar.vue';
import AnnouncementCarousel from './components/AnnouncementCarousel.vue';
import ProductCard from './components/ProductCard.vue';
import CollectionToolbar from './components/CollectionToolbar.vue';
import SectionFooter from './components/SectionFooter.vue';
import ProductFilterSidebar from './components/ProductFilterSidebar.vue';
import SearchBar from './components/SearchBar.vue';
import WhatsappRedirect from './components/WhatsappRedirect.vue';
import ProductCounter from './components/ProductCounter.vue';
import HomePageMenBanner from "./components/HomePageMenBanner.vue";
import ProductFilterMobileOverlay from "./components/ProductFilterMobileOverlay.vue";

export default defineComponent({
  components: {
    HeaderBar, HomePageMenBanner,Paginate, AnnouncementCarousel, ProductCard, CollectionToolbar, SectionFooter, ProductFilterSidebar, ProductFilterMobileOverlay, SearchBar, WhatsappRedirect, ProductCounter
  },
  data() {
    return {
      currentCollectionId: collectionId as string,
      isLoading: true as boolean,
      searchValue: 'mens kurta' as string,
      searchFilter: { result: {} } as any,
      searchResult: { result: {} } as any,
      intialResult: null as any,
      isSearchEnable: false as boolean,
      currSort: 'all_products_search_position' as string,
      isFilterSidebar: false,
      isFilterMobile: false,
      isSortVisible: false,
      isSortMobile: false,
      isEmpty: false,
      pageNum: 0 as number,
      searchFields: ["title",
                    "id",
                    "isActive",
                    "image",
                    "images",                 
                    "discounted_price",                 
                    "collections",
                    "st_express_delivery",
                    "price",
                    "discount",
                    "handle",
                    "hasMultiplePrice",
                    "variants",
                    "vendor",
                    "size",
                    "tags",
                    "voyagerAbsoluteDiscount",
                    "st_sale_discount",
                    "meta_subclass",
                    "st_tags",
                    "material",
                    "meta_collection",
                    "color",
                    "st_sub_category",
                    "st_category",
                    "product_type",
                    "searchtap_subcategory",
                    "st_color",
                    "options"],
      filterObject: {} as Record<string, string[]>,
      productCardWidth: '25%',
    };
  },
  async mounted(){
    this.searchOperation(this.searchValue);
  },
  methods: {
    skipValue(pageNumber: number) {
      this.pageNum = (pageNumber - 1) * 40;
    },
    updateActiveFilters(activeFilters: Record<string, string[]>) {
      this.filterObject = activeFilters;
      this.searchOperation(this.searchValue);
    },
    selectedSortOp(selectedValue: string){
      if(selectedValue === 'created-descending'){
        this.currSort = "all_products_search_position"
      } else if(selectedValue === "whatsnew"){
        this.currSort = "-created_at";
      } else if(selectedValue === "lowestPrice"){
        this.currSort = "discounted_price";
      } else if (selectedValue === "highestPrice") {
        this.currSort = "-discounted_price"
      }
      this.searchOperation(this.searchValue);
    },
    paginationHandler(pageNum: number){
      let val = pageNum;
      console.log(pageNum);
      this.skipValue(val) 
      
      window.scrollTo({
                top: 700,
                left: 0,
                behavior: 'smooth',
      });
      this.searchOperation(this.searchValue);

    },
    updateProductCardWidth(widthPercentage: number){
      this.productCardWidth = `${widthPercentage}%`;
      console.log(`Setting product card width to: ${this.productCardWidth}`);
    },
    closeSearchBar(){
      this.isSearchEnable = false;
    },
    enableSearchBar(){
      if(this.isSearchEnable === true){
        this.isSearchEnable = false;
      } else {
        this.isSearchEnable = true;
      }
    },
    toggleSortState(){
      if(this.isSortVisible){
        this.isSortVisible = false;
      } else {
        this.isSortVisible = true;
      }
    },
    toggleVisibility(){
      if(this.isFilterSidebar){
        this.isFilterSidebar = false;
        if(document.body.classList.contains('overflow-hidden')){
            document.body.classList.remove('overflow-hidden'); 
          }
      } else {
        console.log('button clicked to toggle on')
         this.isFilterSidebar = true;
         if(!document.body.classList.contains('overflow-hidden')){
            document.body.classList.add('overflow-hidden'); 
          }
      }
    },
    toggleVisibilityMobile(){
      if(this.isFilterMobile){
        this.isFilterMobile = false;
      } else {
        console.log('button clicked to toggle on')
         this.isFilterMobile = true;
      }
    },
    async searchOperation(searchVal: string){
      try {
          this.searchValue = searchVal
          this.isLoading = true;
          console.log("Search Operation");
          let searchBuilder = await searchClient
                                    .count(40)
                                    .fields(
                                      ...this.searchFields)
                                    .textFacets(
                                      "stCollectionCategory",
                                      "size",
                                      "st_category",
                                      "st_color",
                                      "st_material",
                                      "st_sub_category",
                                      "st_by_pattern",
                                      "st_bottomwear_fit",
                                      "st_sleeve",
                                      "st_ocassion",
                                      "st_topwear_fit",
                                      "meta_length")
                                    .facetCount(99)
                                    .sort(
                                      "-isActive", 
                                      this.currSort, 
                                      "-_rank")
                                      .numericFacets("discount", [
                                          { min: 10, max: 100, minInclusive: true, maxInclusive: false },
                                          { min: 20, max: 100, minInclusive: true, maxInclusive: false },
                                          { min: 30, max: 100, minInclusive: true, maxInclusive: false },
                                          { min: 40, max: 100, minInclusive: true, maxInclusive: false },
                                          { min: 50, max: 100, minInclusive: true, maxInclusive: false },
                                          { min: 60, max: 100, minInclusive: true, maxInclusive: false },
                                          { min: 70, max: 100, minInclusive: true, maxInclusive: false },
                                          { min: 80, max: 100, minInclusive: true, maxInclusive: false },
                                          { min: 90, max: 100, minInclusive: true, maxInclusive: false },
                                      ])
                                      .numericFacets("discounted_price", [
                                          { min: 0, max: 1000, minInclusive: true, maxInclusive: false },
                                          { min: 1001, max: 2000, minInclusive: true, maxInclusive: false },
                                          { min: 2001, max: 3000, minInclusive: true, maxInclusive: false },
                                          { min: 3001, max: 4000, minInclusive: true, maxInclusive: false },
                                          { min: 4001, max: 5000, minInclusive: true, maxInclusive: false },
                                          { min: 5001, max: 10000, minInclusive: true, maxInclusive: false },
                                          { min: 10001, max: 2000000, minInclusive: true, maxInclusive: false },
                                      ])
                                    .skip(this.pageNum)
                                    .searchFields('*')
                                    .filter("isSearchable = 1 AND isActive = 1 AND discounted_price > 0")
                                         
          for (const category in this.filterObject) {
            const values = this.filterObject[category];
            if (values && values.length > 0) {
              searchBuilder = searchBuilder.textFacetFilters(category, values);
            }
          } 
          const result = await searchBuilder.search(searchVal, collectionId)                         


          const safeResult = result ||  null; 
            
          this.searchResult = safeResult;
          console.log(`${"SearchResulty for keyword " + searchVal + " and SearchResult is "+ safeResult.result + "and Value is skip"+ this.skipValue}`)
          if(safeResult){
            this.searchFilter = safeResult.textFacets;
          }

          if(safeResult === 0) {
            this.isEmpty = true;
          } else {
            this.isEmpty = false;
          }
          
          // console.log(JSON.stringify(safeResult, null, 2));
        } catch (error){
          console.log("Search failed:", error);
          this.searchResult =  null; 

        }finally {
          this.isLoading = false;
        }
    },
    handleRemoveTag(tagInfo: {category: string, value: string}){
      const {category, value} = tagInfo;
      if(this.filterObject[category]) {
        this.filterObject[category] = this.filterObject[category].filter(
          (item: string) => item !== value
        );
        if(this.filterObject[category].length === 0){
          delete this.filterObject[category];
        };
      }
      this.searchOperation(this.searchValue);
    },
    handleClearAllTags(){
      this.filterObject = {};
      this.searchOperation(this.searchValue);
    },
  }
})

</script>