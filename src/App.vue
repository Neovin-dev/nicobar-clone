<template>
  <AnnouncementCarousel />
  <HeaderBar 
      @enable-search-bar="enableSearchBar"
  />
  <SearchBar 
      v-show="isSearchEnable" 
      :active-search="isSearchEnable"
      @close-search-bar="closeSearchBar"
      @update-search="searchOperation"
      @entered-search="searchStringVal"
  />
  <div v-if="bannerEnable" >
      <HomePageMenBanner @filter-state="toggleVisibility"/>
  </div>

  <CollectionToolbar 
          v-if="!(searchResult.totalHits === 0) && searchValue.length && enteredSearch.length > 0 "
          @handle-sort="selectedSortOp"
          @filter-state="toggleVisibility"
          :sort-visible="isSortVisible" 
          @sort-state="toggleSortState"
          :display-data="searchResult"
          @grid-changer="updateProductCardWidth"
          :filter-tags="filterObject"
          @remove-filter-tag="handleRemoveTag"           
          @clear-all-filter-tags="handleClearAllTags"
  />

  <div class="card-container flex flex-[100%] flex-wrap mt-2">

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

    <div class="no-results w-full" v-if="!isLoading && searchResult.totalHits === 0">
      <div class="w-full flex  flex-col justify-center items-center" v-if="searchResult.totalHits === 0">
          <div class="container flex-col items-center flex justify-center w-[280px]">
            <div class="no-result-img flex flex-col w-full justify-center items-center"><img src="../public/image.png" alt=""></div> 
            <h2 class="page-heading flex flex-col w-100 justify-center items-center">Sorry, we can’t find any result</h2> 
            <span class="overflow-hidden whitespace-nowrap text-ellipsis w-[250px] flex justify-center items-center"> for "{{ searchValue }}"</span>
            <div class="search-pform flex flex-col w-100 justify-center items-center">
              <p> Please try a different term. <span style="display: none;">or try <a class="highlight-text">clearing</a> some filters</span>
              </p>
            </div>
          </div> 
          <div></div>
        <div class="flex items-center justify-center text-[20px] border-b border-[#d1cece]">OR</div>
        <div></div>
        <div class="flex flex-col items-center justify-center mt-4">
          <div class="flex items-center justify-center gap-2">
            <svg class="mt-2" width="16" height="20" viewBox="0 0 12 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M7.80968 15.0679C9.5273 12.1176 8.80817 8.40483 6.09966 6.24033C6.09808 6.23911 6.0965 6.23758 6.09523 6.23666L6.10694 6.26482L6.10504 6.28594C6.63276 7.63466 6.55873 9.11531 5.91047 10.3857L5.45362 11.2813L5.31347 10.2917C5.21824 9.62039 4.95659 8.98001 4.55353 8.43177H4.48994L4.4564 8.33993C4.46115 9.3657 4.23778 10.3762 3.7996 11.3294C3.22474 12.5768 3.30922 14.0152 4.02581 15.1778L4.52031 15.9804L3.63066 15.6168C2.16361 15.0171 0.990804 13.8618 0.412783 12.4473C-0.234842 10.8678 -0.114934 9.03633 0.733906 7.54925C1.17652 6.77572 1.48657 5.95443 1.65583 5.10773L1.82129 4.27787L2.24334 5.01804C2.44487 5.37098 2.59326 5.75301 2.68532 6.15432L2.69481 6.16381L2.70462 6.22809L2.71379 6.22533C3.97804 4.6002 4.73545 2.57805 4.84586 0.530486L4.87434 0L5.33435 0.290191C7.21173 1.47391 8.51552 3.37301 8.91827 5.5069L8.92744 5.55067L8.93219 5.5574L8.95275 5.52924C9.3207 5.05906 9.51496 4.4998 9.51496 3.91115V2.99956L10.0835 3.72626C11.4053 5.41537 12.083 7.51068 11.9919 9.62651C11.8799 12.117 10.4761 14.3029 8.23648 15.4873L7.26678 16L7.80968 15.0679Z" fill="#FFA200"></path></svg>
          <h2 class="text-[20px] mt-3">EXPLORE Trending Searches</h2>
          </div>
          
          <p class="flex items-center justify-center mt-2 mb-2">in "Mens Collection"</p>
        </div>
      </div>
        
        <div class="card-container flex flex-[100%] flex-wrap mt-2">
        <ProductCard 
          v-for="product in emptySearchResult.results" 
          :key="product.id"
          :product-data="product"
          :product-card-width="productCardWidth"
        />
        </div>
    </div>
    
  </div>
  
  <div class="pagination-wrapper w-full flex justify-center mb-20 mt-7.5 ">
      <paginate
        v-if="!(searchResult.totalHits === 0) && !isLoading && searchValue.length != 0"
        v-model="currentPage"
        class="flex items-center gap-3 text-[#6A6A6A] my-5"
        :page-count= "Math.ceil(searchResult.totalHits? searchResult.totalHits/40: 0)"
        :click-handler="paginationHandler"
        :prev-text="'<'"
        :next-text="'>'"
        :container-class="'pagination-element'"
        :page-class="'page-item'"
      ></paginate>
  </div>
    
  <SectionFooter />

  <div>
    <transition name="sidebar-slide">
    <ProductFilterSidebar 
        v-if="isFilterSidebar"
        @close-filter-bar="toggleVisibility" 
        :filter-data="searchFilter"
        @search-filters-active="updateActiveFilters"
    />
    </transition>
    <!-- @search-filters-active="editFilters" -->
  </div>
  
    <div v-if="isSortMobile" @click="toggleSortStateMobile" class="overlay w-full h-full bg-[#00000080] fixed top-0 bottom-0 z-12"></div>
    <div v-if="widthMobile" class="collectionToolbarFilterSortMobile h-15 align-middle fixed flex bottom-0 w-full bg-white flex-[100%] py-2 px-5 z-20">
      <div @click="toggleSortStateMobile" class="collectionToolbarSort inline-flex py-2 px-6 border-2 mx-3 border-solid font-bold border-[#dfe1e3] rounded-full justify-center items-center relative cursor-pointer hover:bg-[#ebedf1] flex-[50%]">
          <div class="sort-by-select-header flex text-center text-[10px]">
              <span class="title-text text-[#1A1F29] uppercase">
                Sort by
              </span>
          </div>
        </div>
        <Transition
        enter-from-class="opacity-0 translate-y-40"
        enter-active-class="transition-all duration-300 ease-out"
        enter-to-class="opacity-100 translate-y-0"
        leave-from-class="opacity-100 translate-y-0"
        leave-active-class="transition-all duration-200 ease-in"
        leave-to-class="opacity-0 translate-y-40"
        >
          <ul v-if="isSortMobile" @click="handleSortMobile" class="flex flex-col sort-by-data absolute bottom-15 left-0 bg-white text-left text-[10px] text-[#1a1f29] z-9 w-full float-left shadow-[1px_1px_4px_#7070704d] m-0 cursor-pointer">
                  <!-- <li @click="toggleSortStateMobile" value="title" class="data first-child tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid uppercase" data-index="3" data-value="title" ><span>Sort By</span></li> -->

                  <li @click="toggleSortStateMobile" value="created-descending" class="data first-child tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="3" data-value="created-descending" :class="{ 'bg-[#ebedf1] hover:bg-[#ebedf1] border-l-4 border-l-[#9ea5ad]': ActiveSortApplied === 'Featured' }" ><span>Featured</span></li>

                  <li @click="toggleSortStateMobile"  value="whatsnew" class="data is-selected tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="0" data-value="whatsnew" :class="{ 'bg-[#ebedf1]  hover:bg-[#ebedf1] border-l-4 border-l-[#9ea5ad]': ActiveSortApplied === 'What\'s New' }"
                  ><span>What's New</span></li>

                  <li @click="toggleSortStateMobile"  value="lowestPrice" class="data tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="1" data-value="lowestPrice" :class="{ 'bg-[#ebedf1]  hover:bg-[#ebedf1] border-l-4 border-l-[#9ea5ad]': ActiveSortApplied === 'Lowest Price' }"><span>Lowest Price</span></li>

                  <li @click="toggleSortStateMobile"  value="highestPrice" class="data tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="2" data-value="highestPrice" :class="{ 'bg-[#ebedf1]  hover:bg-[#ebedf1] border-l-4 border-l-[#9ea5ad]': ActiveSortApplied === 'Highest Price' }"><span>Highest Price</span></li>
          </ul>
        </Transition>
      <div @click="toggleVisibility" class="filter-container flex mx-3 flex-[50%]" >
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

type sortOptions = 'Featured' | "What's New" | 'Lowest Price' | 'Highest Price';

export default defineComponent({
  components: {
    HeaderBar, 
    HomePageMenBanner,
    Paginate, 
    AnnouncementCarousel, 
    ProductCard, 
    CollectionToolbar, 
    SectionFooter, 
    ProductFilterSidebar, 
    SearchBar, 
    WhatsappRedirect, 
    ProductCounter
  },
  data() {
    return {
      currentCollectionId: collectionId as string,
      isLoading: true as boolean,
      initialsearchValue: 'mens kurta' as string,
      searchValue: '' as string,
      searchFilter: { result: {} } as any,
      searchResult: { result: {} } as any,
      searchResultCopy: { result: {} } as any,
      intialResult: null as any,
      isSearchEnable: false as boolean,
      currSort: 'all_products_search_position' as string,
      isFilterSidebar: false,
      isFilterMobile: false,
      isSortVisible: false,
      isSortMobile: false,
      isEmpty: false,
      pageNum: 1 as number,
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
      widthMobile: window.innerWidth <= 1024,
      ActiveSortApplied: 'Featured' as sortOptions,
      currentPage: 1 as number,
      bannerEnable: true as boolean,
      emptySearchResult: { result: {} } as any,
      emptyStateSearch: 'mens collection',
      enteredSearch: '' as string,
    };
  },
  async mounted(){
    this.searchOperation(this.initialsearchValue);
    // this.searchOperation(this.emptyStateSearch);
  },
  methods: {
    searchStringVal(val: string){
      this.enteredSearch = val;
    },
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
    handleSortMobile(event: Event){
        const targetli = (event.target as HTMLElement).closest('li');
        if(targetli){
          const selectedValue = targetli.getAttribute('value');
          const selectedText = targetli.querySelector('span')?.textContent;
          if(targetli){
            this.ActiveSortApplied = selectedText as sortOptions;
            // this.toggleSortStateMobile();
          }
          this.selectedSortOp(selectedValue as string);
        }
      },
    paginationHandler(pageNum: number){
      this.currentPage = pageNum;
      console.log(this.currentPage);
      this.skipValue(pageNum) 
      
      setTimeout(() => {
        window.scrollTo({
                top: 600,
                left: 0,
                behavior: 'smooth',
        });
      }, 200);
      

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
    toggleSortStateMobile(){
      if(this.isSortMobile){
        if(document.body.classList.contains('overflow-hidden')){
            document.body.classList.remove('overflow-hidden'); 
          }

        this.isSortMobile= false;
      } else {
        document.body.classList.add('overflow-hidden'); 
        
        this.isSortMobile = true;
      }
    },
    toggleVisibility(){
      if(this.isFilterSidebar){
        this.isFilterSidebar = false;
        if(document.body.classList.contains('overflow-hidden')){
            document.body.classList.remove('overflow-hidden'); 
          }
        setTimeout(() => {
          window.scrollTo({
                  top: 600,
                  left: 0,
                  behavior: 'smooth',
          });
        }, 200);
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
        this.enteredSearch = searchVal ;
        const isSearchNew = this.searchValue !== searchVal;

        if(isSearchNew){
          this.filterObject = {};
          this.currSort = 'all_products_search_position';
          this.ActiveSortApplied = "Featured" as sortOptions;
          this.currentPage = 1;
          this.pageNum = 0;
        };

        if(searchVal === 'mens kurta'){
          this.bannerEnable = true;
        } else {
          this.bannerEnable = false;
        }
          
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
          // this.currentPage = 1;

          
          const result = await searchBuilder.search(searchVal, collectionId)                         

          const safeResult = result ||  null; 
            
          

          if(searchVal === 'mens collection'){
            this.emptySearchResult = safeResult
          } else {
            this.searchResult = safeResult;
          }
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
  },
  watch: {
    'searchResult.totalHits': {
      handler(totalHits){
        if(totalHits === 0){
          this.searchOperation(this.emptyStateSearch);
        } else {
          console.log("successful search result")
        }
      }
    }
  }
})

</script>

<style>

.collectionToolbarFilterSortMobile {
  box-shadow: 1px -8px 31px 11px rgba(188,188,188,0.72);
-webkit-box-shadow: 1px -8px 31px 11px rgba(188,188,188,0.72);
-moz-box-shadow: 1px -8px 31px 11px rgba(188,188,188,0.72);
}

.sidebar-slide-enter-from .overlay,
.sidebar-slide-leave-to .overlay {
  opacity: 0;
}

.sidebar-slide-enter-to .overlay,
.sidebar-slide-leave-from .overlay {
  opacity: 1;
}

.sidebar-slide-enter-from .product-filter-sidebar,
.sidebar-slide-leave-to .product-filter-sidebar {
  transform: translateX(100%);
}

.sidebar-slide-enter-to .product-filter-sidebar,
.sidebar-slide-leave-from .product-filter-sidebar {
  transform: translateX(0);
}

@media (max-width: 1024px) {
  .sidebar-slide-enter-from .product-filter-sidebar,
  .sidebar-slide-leave-to .product-filter-sidebar {
    transform: translateY(100%);
  }
}


@media (max-width: 468px){
  .no-result-img {
    width: 200px;
  }
}
</style>