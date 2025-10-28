<script setup lang="ts">
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
</script>

<template>
  <AnnouncementCarousel />
  <HeaderBar />
  <CollectionBanner />
  <TopCarousel />
  <ExpressBanner />
  <ProductCardBanner />
  <CollectionToolbar />

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
  
  <PaginationSection />
  <SectionFooter />
  
</template>

<style scoped>
</style>