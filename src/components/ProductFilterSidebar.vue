<template>
    <div class="product-filter-sidebar absolute top-0 right-0 h-full bg-white h-100% w-[375px] px-5 py-7.5">
    <div class="filter-bar-header">
      Express Delivery
    </div>
    <div class="filter-desc">
      Enter your PIN Code 
    </div>
  <div class="filter-header">
    <h3 class="filter-title">Size</h3>
  </div>

  <div class="filter-options-list">
    <ul class="size-options">
      <li class="filter-option-item">
        <label for="Filter-Size-XS" class="facet-checkbox-label">
          <input type="checkbox" name="filter.v.option.size" value="XS" id="Filter-Size-XS" class="size-checkbox">
          <span class="filter-item-value">XS</span>
          <span class="filter-item-count">(13)</span>
        </label>
      </li>

      <li class="filter-option-item">
        <label for="Filter-Size-S" class="facet-checkbox-label">
          <input type="checkbox" name="filter.v.option.size" value="S" id="Filter-Size-S" class="size-checkbox">
          <span class="filter-item-value">S</span>
          <span class="filter-item-count">(209)</span>
        </label>
      </li>

      <li class="filter-option-item">
        <label for="Filter-Size-M" class="facet-checkbox-label">
          <input type="checkbox" name="filter.v.option.size" value="M" id="Filter-Size-M" class="size-checkbox">
          <span class="filter-item-value">M</span>
          <span class="filter-item-count">(170)</span>
        </label>
      </li>

      <li class="filter-option-item">
        <label for="Filter-Size-L" class="facet-checkbox-label">
          <input type="checkbox" name="filter.v.option.size" value="L" id="Filter-Size-L" class="size-checkbox">
          <span class="filter-item-value">L</span>
          <span class="filter-item-count">(184)</span>
        </label>
      </li>

      <li class="filter-option-item">
        <label for="Filter-Size-XL" class="facet-checkbox-label">
          <input type="checkbox" name="filter.v.option.size" value="XL" id="Filter-Size-XL" class="size-checkbox">
          <span class="filter-item-value">XL</span>
          <span class="filter-item-count">(182)</span>
        </label>
      </li>
      
      <li class="filter-option-item">
        <label for="Filter-Size-2XL" class="facet-checkbox-label">
          <input type="checkbox" name="filter.v.option.size" value="2XL" id="Filter-Size-2XL" class="size-checkbox">
          <span class="filter-item-value">2XL</span>
          <span class="filter-item-count">(176)</span>
        </label>
      </li>

      <li class="filter-option-item">
        <label for="Filter-Size-3XL" class="facet-checkbox-label">
          <input type="checkbox" name="filter.v.option.size" value="3XL" id="Filter-Size-3XL" class="size-checkbox">
          <span class="filter-item-value">3XL</span>
          <span class="filter-item-count">(225)</span>
        </label>
      </li>
      
      <li class="filter-option-item">
        <label for="Filter-Size-32" class="facet-checkbox-label">
          <input type="checkbox" name="filter.v.option.size" value="32" id="Filter-Size-32" class="size-checkbox">
          <span class="filter-item-value">32</span>
          <span class="filter-item-count">(43)</span>
        </label>
      </li>

    </ul>
  </div>

  <div class="filter-actions-footer fixed bottom-0 flex flex-col w-[375px] pb-7.5 px-5 pr-10">
    <div class="footer-selector flex gap-2">
      <p class="total-selected-filters"><span class="active-count">1</span> filters selected</p>
      <button class="clear-all-filters-btn text-left">Clear filters</button>
    </div>
    <div class="flex flex-[100%]">
      <button class="close-filter-btn inline-flex flex-[50%] py-2 px-6 border-2 border-solid border-[#dfe1e3] rounded-full justify-center items-center text-[10px]">Close</button>
      <button class="apply-filter-btn inline-flex flex-[50%] py-2 px-6 border-2 border-solid border-[#dfe1e3] rounded-full justify-center items-center text-[10px]">See items</button>
    </div>
  </div>
</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";


export default defineComponent ({
    name: 'ProductFilterSidebar'
})
</script>