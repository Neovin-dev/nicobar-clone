#AF041B
#000000
banner color

<div v-if="(displayData.query.query !== "mens kurta")" class="searchBanner">
        Showing {{ displayData.totalHits ? displayData.totalHits: 'Loading..'  }} products for "{{displayData.query.query ? displayData.query.query : "Loading.. " }}"
    </div>


    <div class="st-filter-tag-list px-9 py-4 flex text-[11px] flex-wrap">
    <div class="st-filter-tag flex flex-wrap">
        <template v-for="(values, category) in filterTags" :key="category">
            <div 
              v-for="value in values" 
              :key="category + '-' + value"
              class="st-filter-tag-wrapper inline-flex rounded-full px-2 py-1 mr-2 items-center bg-[#ECECEC] mb-2"
            >
            <span class="st-tag-text pr-2">{{ value }}</span>
                <a 
                    class="tag-icon cursor-pointer" 
                    @click="removeFilter(category, value)"
                >
                    <svg role="presentation" viewBox="0 0 16 14" class="Icon Icon--close w-2 h-2">
                        <path d="M15 0L1 14m14 0L1 0" stroke="currentColor" fill="none" fill-rule="evenodd"></path>
                    </svg>
                </a>
            </div>
        </template>
    </div>
</div>
    <div 
        v-if="hasActiveFilters" 
        class="flex items-center ml-2 underline text-[11px] cursor-pointer"
        @click="clearAllFilters"
    >
        Clear Filters
    </div>
</div>

computed: {
      hasActiveFilters(){
        return this.filterTags.length > 0;
      }
    }