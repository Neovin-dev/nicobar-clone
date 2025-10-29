<template>
  <AnnouncementCarousel />
  <HeaderBar 
      @enable-search-bar="enableSearchBar"
  />
  <SearchBar 
      v-if="isSearchEnable" 
      @close-search-bar="closeSearchBar"
  />
  <div v-else>
    <CollectionBanner />
      <TopCarousel />
      <ExpressBanner />
      <ProductCardBanner />
      <CollectionToolbar />
  </div>
  
  <div class="card-container flex flex-[100%] flex-wrap">
    <div class="loading-overlay" v-if="isLoading">Loading Products...</div>
    
    <ProductCard 
        v-else-if="!isLoading"
        v-for="product in searchResult.results" 
        :key="product.id"
        :product-data="product"
    />

    <div class="no-results w-full" v-else-if="!isLoading">
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
  
  <PaginationSection />
  <SectionFooter />

  <ProductFilterSidebar />
  <ProductCounter />
  <WhatsappRedirect />
  
</template>

<script lang="ts">

// Imports
import SearchClient from "@gaspl/search-client"
import { defineComponent } from "vue";

// Working NICOBAR TOKENS
const searchToken = import.meta.env.VITE_NICOBAR_SEARCH_TOKEN as string;
const applicationId =import.meta.env.VITE_NICOBAR_APPLICATION_ID as string;
const collectionId =import.meta.env.VITE_NICOBAR_COLLECTION_ID as string;

// Client initialization
var searchClient = new SearchClient(applicationId, searchToken);

// Componenet Imports
import CollectionBanner from './components/CollectionBanner.vue';
import HeaderBar from './components/HeaderBar.vue';
import AnnouncementCarousel from './components/AnnouncementCarousel.vue';
import ProductCard from './components/ProductCard.vue';
import TopCarousel from './components/TopCarousel.vue';
import ExpressBanner from './components/ExpressBanner.vue';
import ProductCardBanner from './components/ProductCardBanner.vue';
import CollectionToolbar from './components/CollectionToolbar.vue';
import PaginationSection from './components/PaginationSection.vue';
import SectionFooter from './components/SectionFooter.vue';
import ProductFilterSidebar from './components/ProductFilterSidebar.vue';
import SearchBar from './components/SearchBar.vue';
import WhatsappRedirect from './components/WhatsappRedirect.vue';
import ProductCounter from './components/ProductCounter.vue';


export default defineComponent({
  components: {
    CollectionBanner, HeaderBar, AnnouncementCarousel, ProductCard, TopCarousel, ExpressBanner, ProductCardBanner, CollectionToolbar, PaginationSection, SectionFooter, ProductFilterSidebar, SearchBar, WhatsappRedirect, ProductCounter
  },
  data() {
    return {
      isLoading: true as boolean,
      searchValue: '*' as string,
      searchResult: null as any,
      isSearchEnable: false as boolean,

    };
  },
  async mounted(){
    try {
      this.isLoading = true;
      console.log("Componenet Mounted. Started searching");
      const result = await searchClient.search(this.searchValue, collectionId);
      this.searchResult = result;
      console.log(JSON.stringify(result, null, 2));
    } catch (error){
      console.log("Search failed:", error);
    }finally {
      this.isLoading = false;
    }
  },
  methods: {
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

  }
})

</script>

<style scoped>

</style>