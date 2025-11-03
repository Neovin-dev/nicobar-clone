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
  />

  <div class="card-container flex flex-[100%] flex-wrap">

  <div class="loading-overlay w-full flex items-center justify-center h-50" v-if="isLoading">
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

    <div class="no-results w-full" v-else-if="isEmpty">
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
  
  <PaginationSection v-if="!isLoading" />
  <SectionFooter />

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

  <div>
    
  </div>
  
  <ProductCounter 
      :display-data="searchResult" 
  />
  <WhatsappRedirect />
  
</template>

<script lang="ts">

// Imports
import SearchClient from "@gaspl/search-client"
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
import PaginationSection from './components/PaginationSection.vue';
import SectionFooter from './components/SectionFooter.vue';
import ProductFilterSidebar from './components/ProductFilterSidebar.vue';
import SearchBar from './components/SearchBar.vue';
import WhatsappRedirect from './components/WhatsappRedirect.vue';
import ProductCounter from './components/ProductCounter.vue';
import HomePageMenBanner from "./components/HomePageMenBanner.vue";

export default defineComponent({
  components: {
    HeaderBar, HomePageMenBanner, AnnouncementCarousel, ProductCard, CollectionToolbar, PaginationSection, SectionFooter, ProductFilterSidebar, SearchBar, WhatsappRedirect, ProductCounter
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
      isSortVisible: false,
      isEmpty: false,
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
    // editFilters(filtersObj: string) {
    //   // console.log('filtersObj',filtersObj);
    //   // let allFilterValuesString = '' as string;
    //   // Object.keys(filtersObj).forEach((category: string) => {
    //   //   console.log('Category', category);
    //   //   const selectedValues: string[] = filtersObj[category];
    //   //   const categoryValuesString = selectedValues.join(', ')
    //   //   // allFilterValuesString += `${category}: ${categoryValuesString} | `;
    //   //   allFilterValuesString += `${categoryValuesString}, `
    //   // })
    //   // console.log('allFilterValues', allFilterValuesString);
      
    // },
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
          if(safeResult){
            this.searchFilter = safeResult.textFacets;
          }

          if(safeResult === 0) {
            this.isEmpty = true;
          } else {
            this.isEmpty = false;
          }
          
          console.log(JSON.stringify(safeResult, null, 2));
        } catch (error){
          console.log("Search failed:", error);
          this.searchResult =  null; 

        }finally {
          this.isLoading = false;
        }
    }
    
  }
})

</script>