<template>
  <div class="z-50">
    <div class="overlay w-full h-full bg-[#00000080] fixed top-0 bottom-0 " @click="closeFilterBar"></div>
      <div class="product-filter-sidebar fixed top-0 right-0 h-screen bg-white w-[375px] px-5 py-7.5 z-11">
        <div class="filter-bar-header mb-1.75 text-[14px] uppercase text-[#5b6670] font-medium ml-[-3px]">
          Express Delivery
        </div>
        <div class="filter-desc font-light text-[11px] mb-3.75 pb-3 ml-[-3px]">
          Enter your PIN Code 
        </div>

        <div class="overflow-y-auto h-150" v-if="filterData && filterData.textFacets">
          
          <div 
            v-for="(options, categoryKey) in filterData.textFacets" 
            :key="categoryKey"
            v-if="options.length > 0" >
            <div class="filter-header flex p-3 border-t-[#ebedf1] border-t border-solid border-b-[#ebedf1] border-b">
              <div class="pr-3 flex items-center justify-center font-bold text-[#5b6670] h-5">+</div>
              <h3 class="filter-title uppercase text-[#5b6670] cursor-pointer font-bold text-[14px]">
                {{ FilterTitleFormatter(categoryKey) }}
              </h3>
            </div>

            <div class="filter-options-list flex">
              <ul :class="categoryKey === 'size' ? 'size-options flex flex-wrap' : 'default-options-list p-4'">
                
                <li 
                  class="filter-option-item" 
                  v-for="option in options" 
                  :key="option.label"
                >
                  <label :for="'Filter-' + categoryKey + '-' + option.label" class="facet-checkbox-label text-[10px]">
                    <input 
                      type="checkbox" 
                      :name="'filter.' + categoryKey" 
                      :value="option.label" 
                      :id="'Filter-' + categoryKey + '-' + option.label"
                      class="size-checkbox"
                      @change="handleFilterChange(categoryKey, option.label, $event)"
                    >
                    <span class="filter-item-value pr-2">{{ option.label }}</span>
                    <span class="filter-item-count">({{ option.value }})</span>
                  </label>
                </li>

              </ul>
            </div>
          </div>
        </div>
        <div class="filter-actions-footer fixed bottom-0 flex flex-col w-[375px] pb-7.5 px-5 pr-10 bg-white">
          <div class="footer-selector flex gap-2 pb-2">
            <p class="total-selected-filters text-sm"><span class="active-count">1</span> filters selected</p>
            <button class="clear-all-filters-btn text-left text-sm text-amber-200">Clear filters</button>
          </div>
          <div class="flex flex-[100%]">
            <button @click="closeFilterBar" class="close-filter-btn inline-flex flex-[50%] py-2 px-6 border-2 border-solid border-[#dfe1e3] rounded-full justify-center items-center text-[10px]">Close</button>
            <button @click="applyFilters" class="apply-filter-btn inline-flex flex-[50%] py-2 px-6 border-2 border-solid border-[#dfe1e3] rounded-full justify-center items-center text-[10px]">See items</button>
          </div>
        </div>
      </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent ({
    name: 'ProductFilterSidebar',
    props: {
      filterData: {
        type: Object,
        required: true,
      },
    },
    data() {
      return {
          selectedFilters: {} as Record<string, string[]>
          }
        },
    emits: ['close-filter-bar', 'apply-filters'],
    methods: {
      closeFilterBar(){
        this.$emit('close-filter-bar')
      },
      FilterTitleFormatter(key: string): string {

        if (key === 'size') return 'Size';
        if (key === 'st_color') return 'Color';
        if (key === 'meta_length') return 'Length';
        if (key === 'st_material') return 'Material';
        if (key === 'st_ocassion') return 'Occasion';
        if (key === 'st_sub_category') return 'Sub Category';
        if (key === 'st_by_pattern') return 'Pattern';
        if (key === 'st_sleeve') return 'Sleeve';
        if (key === 'st_topwear_fit') return 'Top Fit';
        if (key === 'st_bottomwear_fit') return 'Bottom Fit';
        if (key === 'st_category') return 'Category';
        return key
          .replace('st_', '')
          .split('_')
          .map((word: string) => word.charAt(0).toUpperCase() + word.slice(1))
          .join(' ');
      },
      handleFilterChange(categoryKey: string, optionLabel: string, event: Event) {
        const isChecked = (event.target as HTMLInputElement).checked;

        if (!this.selectedFilters[categoryKey]) {
          this.selectedFilters[categoryKey] = [];
        }
        
        if (isChecked) {
          this.selectedFilters[categoryKey].push(optionLabel);
        } else {
          const index = this.selectedFilters[categoryKey].indexOf(optionLabel);
          if (index > -1) {
            this.selectedFilters[categoryKey].splice(index, 1);
          }
        }
      },
      applyFilters() {
        this.$emit('apply-filters', this.selectedFilters);
      }
    },
})
</script>

<style>
/* input[type="checkbox"] {
    padding: 0;
    height: 20px;
    width: 20px;
    border-radius: 0;
    margin: 0 10px;
} */

input[type="checkbox"] { 
  appearance: none;
  -webkit-appearance: none;
  /* opacity: 0; */
}

label {
  position:relative;
  padding-left: 25px;
  cursor: pointer;
  display: inline-flex;
}

 label > input[type="checkbox"]::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 0;
  cursor: pointer;
  transform: translateY(-50%);
  width: 16px;
  height: 16px;
  border: 1px solid #555;
  background-color: #fff;
  border-radius: 2px;
}

label > input[type="checkbox"]:checked::before {
    background-color: #292b30;
    border-color: #292b30;
}

label > input[type="checkbox"]:checked::after {
  content: url('data:image/svg+xml;charset=utf8,<svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M4.89163 13.2687L9.16582 17.5427L18.7085 8" stroke="%23FFFFFF" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/></svg>');
  position: absolute;
  top: 50%;
  left: 0;
  transform: translate(-0%, -50%);
  height: 15px;
  width: 15px;
}

.filter-option-item {
  width: 140px;
}


.size-options:first-child {
  margin-top: 10px;
}
</style>