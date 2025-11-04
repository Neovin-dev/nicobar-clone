<template>
<div class="collectionToolbar flex-[100%] py-0.5 px-3.75 flex justify-between pt-4 sticky top-0 bg-white z-5 mb-0.5 w-full">
    <div class="collectionToobarView flex-[30%] flex flex-row py-2">
      <div v-if="widthValue== true" class="viewOrientationSidepanelDesktop flex flex-row">
          <button @click="gridChangerfour" aria-label="Show four products per row" class="CollectionToolbar-layout-four h-5 w-5 flex justify-center align-middle cursor-pointer" data-action="change-layout-mode" data-grid-type="desktop" data-count="4" fdprocessedid="b0xfnh">
            <svg v-if="gridView === 'four'" class="Icon Icon--wall-2" role="presentation">
              <g id="grid4" transform="translate(-73 -520)">

                <rect id="Rectangle_283" data-name="Rectangle 283" width="6" height="6" transform="translate(73 520)" fill="#1c1b1b"></rect>
                <rect id="Rectangle_284" data-name="Rectangle 284" width="6" height="6" transform="translate(82 520)" fill="#1c1b1b"></rect>
                <rect id="Rectangle_285" data-name="Rectangle 285" width="6" height="6" transform="translate(82 529)" fill="#1c1b1b"></rect>
                <rect id="Rectangle_286" data-name="Rectangle 286" width="6" height="6" transform="translate(73 529)" fill="#1c1b1b"></rect>
              </g>
            </svg>
            <svg v-else class="Icon Icon--wall-2" role="presentation">
              <g id="grid4" transform="translate(-73 -520)">
                <rect id="Rectangle_283" data-name="Rectangle 283" width="6" height="6" transform="translate(73 520)" fill="#bcbcbc"></rect>
                <rect id="Rectangle_284" data-name="Rectangle 284" width="6" height="6" transform="translate(82 520)" fill="#bcbcbc"></rect>
                <rect id="Rectangle_285" data-name="Rectangle 285" width="6" height="6" transform="translate(82 529)" fill="#bcbcbc"></rect>
                <rect id="Rectangle_286" data-name="Rectangle 286" width="6" height="6" transform="translate(73 529)" fill="#bcbcbc"></rect>
              </g>
            </svg>
          </button>

          <button @click="gridChangertwo" aria-label="Show two products per row" class="CollectionToolbar-layout-two h-5 w-5 flex justify-center align-middle cursor-pointer" data-action="change-layout-mode" data-grid-type="desktop" data-count="2" fdprocessedid="vbsbq8">
            <svg v-if="gridView === 'two'" class="Icon Icon--wall-4 h-5 w-5" role="presentation">
              <g xmlns="http://www.w3.org/2000/svg" id="grid2" transform="translate(-73 -520)">
                <rect id="Rectangle_283" data-name="Rectangle 283" width="6" height="15" transform="translate(73 520)" fill="#1c1b1b"></rect>
                <rect id="Rectangle_284" data-name="Rectangle 284" width="6" height="15" transform="translate(82 520)" fill="#1c1b1b"></rect>
              </g>
            </svg>
              <svg v-else class="Icon Icon--wall-4 h-5 w-5" role="presentation">
              <g xmlns="http://www.w3.org/2000/svg" id="grid2" transform="translate(-73 -520)">
                <rect id="Rectangle_283" data-name="Rectangle 283" width="6" height="15" transform="translate(73 520)" fill="#bcbcbc"></rect>
                <rect id="Rectangle_284" data-name="Rectangle 284" width="6" height="15" transform="translate(82 520)" fill="#bcbcbc"></rect>
              </g>
            </svg>
          </button>
      </div>
      <div v-if="widthValue == false" class="viewOrientationSidepanelMobile flex flex-row">
          <button @click="gridChangerone" aria-label="Show one product per row" class="CollectionToolbar__LayoutType h-4 w-4 flex justify-center align-middle cursor-pointer mr-2" data-action="change-layout-mode" data-grid-type="mobile" data-count="1">
            <svg  v-if="gridView === 'one'" class="Icon Icon--wall-1 h-3.75 w-3.75" role="presentation">
              <rect fill="#1c1b1b" width="36" height="36"></rect>
            </svg>
            <svg v-else class="Icon Icon--wall-1 h-3.75 w-3.75" role="presentation">
              <rect fill="#bcbcbc" width="36" height="36"></rect>
            </svg>
          </button>
 
          <button @click="gridChangertwo" aria-label="Show two products per row" class="CollectionToolbar-layout-two h-5 w-5 flex justify-center align-middle cursor-pointer" data-action="change-layout-mode" data-grid-type="desktop" data-count="2" fdprocessedid="vbsbq8">
            <svg v-if="gridView === 'two'" class="Icon Icon--wall-4 h-5 w-5" role="presentation">
              <g xmlns="http://www.w3.org/2000/svg" id="grid2" transform="translate(-73 -520)">
                <rect id="Rectangle_283" data-name="Rectangle 283" width="6" height="15" transform="translate(73 520)" fill="#1c1b1b"></rect>
                <rect id="Rectangle_284" data-name="Rectangle 284" width="6" height="15" transform="translate(82 520)" fill="#1c1b1b"></rect>
              </g>
            </svg>
              <svg v-else class="Icon Icon--wall-4 h-5 w-5" role="presentation">
              <g xmlns="http://www.w3.org/2000/svg" id="grid2" transform="translate(-73 -520)">
                <rect id="Rectangle_283" data-name="Rectangle 283" width="6" height="15" transform="translate(73 520)" fill="#bcbcbc"></rect>
                <rect id="Rectangle_284" data-name="Rectangle 284" width="6" height="15" transform="translate(82 520)" fill="#bcbcbc"></rect>
              </g>
            </svg>
          </button>
      </div>
    </div>
    <div v-if="searchResultMensKurta && widthResolution" class="searchBanner text-[#282b30] flex-[30%] flex items-center uppercase text-[12px]">
        Showing {{ displayData.totalHits ? displayData.totalHits: 'Loading..'  }} products for "{{displayData.query.query ? displayData.query.query : "Loading.. " }}"
    </div>
    <div v-if="searchResultMensKurta && !widthResolution" class="searchBanner text-[#282b30] flex-[50%] flex items-center uppercase text-[12px] justify-end">
        Showing {{ displayData.totalHits ? displayData.totalHits: 'Loading..'  }} products for "{{displayData.query.query ? displayData.query.query : "Loading.. " }}"
    </div>
    
    <div v-if="widthResolution" class="collectionToolbarFilterSort flex align-middle items-center">
      <div  @click="sortState" class="collectionToolbarSort inline-flex py-2 px-4 border-2 border-solid border-[#dfe1e3] rounded-full justify-center items-center relative cursor-pointer hover:bg-[#ebedf1]">
        <div class="sort-by-select-header flex text-center text-[10px] ">
            <span class="title-text text-[#9ea5ad]">
              Sort by:
            </span>
            <span class="active-sort-by flex items-center pl-1 font-bold">
              <span>{{ ActiveSortApplied }}</span>
            </span>
            <div class="chevron-down-icon pl-2 pt-1.5">
              <svg aria-hidden="true" focusable="false" role="presentation" class="icon icon--wide h-1 w-2 "><path xmlns="http://www.w3.org/2000/svg" id="down-arrow" d="M990.5,3700.5l3-3,3,3" transform="translate(997.208 3701.207) rotate(180)" fill="none" stroke="#424a54" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></path></svg>
            </div>
        </div>
        <ul v-if="sortVisible" @click="handleSort" class="min-w-[270px] sort-by-data absolute top-12 bg-white text-left text-[10px] text-[#1a1f29] z-9 w-full float-left shadow-[1px_1px_4px_#7070704d] m-0 -left-10 cursor-pointer">
              <li @click="sortState" value="created-descending" class="data first-child tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="3" data-value="created-descending"
              :class="{ 'bg-[#ebedf1] hover:bg-[#ebedf1] border-l-4 border-l-[#9ea5ad]': ActiveSortApplied === 'Featured' }"
              ><span>Featured</span></li>

              <li @click="sortState" value="whatsnew" class="data is-selected tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="0" data-value="whatsnew"
              :class="{ 'bg-[#ebedf1]  hover:bg-[#ebedf1] border-l-4 border-l-[#9ea5ad]': ActiveSortApplied === 'What\'s New' }"><span>What's New</span></li>

              <li @click="sortState" value="lowestPrice" class="data tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="1" data-value="lowestPrice" :class="{ 'bg-[#ebedf1]  hover:bg-[#ebedf1] border-l-4 border-l-[#9ea5ad]': ActiveSortApplied === 'Lowest Price' }"><span>Lowest Price</span></li>

              <li @click="sortState" value="highestPrice" class="data tracking-[0] font-normal px-5 py-[15px] text-[#1a1f29] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="2" data-value="highestPrice" :class="{ 'bg-[#ebedf1]  hover:bg-[#ebedf1] border-l-4 border-l-[#9ea5ad]': ActiveSortApplied === 'Highest Price' }"><span>Highest Price</span></li>
        </ul>
      
      </div>
      <div class="filter-container flex ml-2.5" @click="filterState" >
        <button class="filter-bar inline-flex py-2 px-6 border-2 border-solid border-[#dfe1e3] rounded-full justify-center items-center text-[10px] hover:bg-[#ebedf1] cursor-pointer">
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
<div v-if="Object.keys(filterTags).length > 0"  class="st-filter-tag-list flex-[30%] px-9 py-4 flex">
  <div class="st-filter-tag flex flex-wrap items-center">
        <template v-for="(values, category) in filterTags" :key="category">
            <div 
              v-for="value in values" 
              :key="category + '-' + value"
              class="st-filter-tag-wrapper inline-flex rounded-full px-2 py-1 mr-2 bg-[#ECECEC] items-center hover:bg-[#9ea5ad] cursor-pointer"
              @click="removeTag(category, value)"
            >
            <span class="st-tag-text pr-2 text-[11px] px-2">{{ value }}</span>
                <a class="tag-icon" >
                    <svg role="presentation" viewBox="0 0 16 14" class="Icon Icon--close w-2 h-2">
                        <path d="M15 0L1 14m14 0L1 0" stroke="currentColor" fill="none" fill-rule="evenodd"></path>
                    </svg>
                </a>
            </div>
        </template>
    </div>
    <div 
        v-if="Object.keys(filterTags).length > 0" 
        class="clear-all-tag flex text-[11px] items-center justify-center underline cursor-pointer"
        @click="clearAllTags"
    >
      Clear All
    </div>
</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

type GridView = 'one'| 'two' | 'four';
type sortOptions = 'Featured' | "What's New" | 'Lowest Price' | 'Highest Price';

export default defineComponent ({
    name: 'CollectionToolbar',
    data(): {gridView : GridView, ActiveSortApplied : sortOptions, widthValue: boolean, searchResultMensKurta: boolean, widthResolution: boolean} {
      return {
        gridView: 'four',
        ActiveSortApplied: 'Featured',
        widthValue: false,
        searchResultMensKurta: false,
        widthResolution: window.innerWidth > 1024,
      };
    },
    emits: [
      'handle-sort', 
      'filter-state', 
      'sort-state', 
      'grid-changer',
      'remove-filter-tag',
      'clear-all-filter-tags'
    ],
    props: {
      displayData: {
        type: Object,
        required: true,
      },
      sortVisible: {
        type: Boolean,
        required: true,
      },
      filterTags: {
        type: Object,
        required: true,
      }
    },
    watch: {
      'displayData.query.query': {
        handler(newQueryValue) {
          if (newQueryValue) {
            if (newQueryValue === 'mens kurta') {
              this.searchResultMensKurta = false;
            } else {
              this.searchResultMensKurta = true;
            }
            } else {
              this.searchResultMensKurta = false;
            }
          },
            immediate: true,
          },
        },
    methods: {
      handleSort(event: Event){
        const targetli = (event.target as HTMLElement).closest('li');
        if(targetli){
          const selectedValue = targetli.getAttribute('value');
          const selectedText = targetli.querySelector('span')?.textContent;
          if(targetli){
            this.ActiveSortApplied = selectedText as sortOptions;
            this.sortState();
          }
          this.$emit('handle-sort', selectedValue);
        }
      },
      gridChangerone(){
        this.gridView = 'one';
        this.$emit('grid-changer', 100);
        console.log(this.displayData);
      },
      gridChangerfour(){
        this.gridView = 'four';
        this.$emit('grid-changer', 25);
        console.log(this.displayData);
      },
      gridChangertwo(){
        this.gridView = 'two';
        this.$emit('grid-changer', 50);
      },
      filterState() {
        this.$emit('filter-state')
        console.log('filter-state-triggered');
      },
      sortState(){
        this.$emit('sort-state')
      },
      removeTag(category: string, value: string){
        this.$emit('remove-filter-tag', {category, value});
      },
      clearAllTags(){
        this.$emit('clear-all-filter-tags');
      }
    },
    mounted(){

      const windowInnerWidth = window.innerWidth;
      let initialGridView: GridView;
      let initialWidth: number;
      if(windowInnerWidth > 1024){
          this.widthValue = true;
          initialGridView = 'four';
          initialWidth = 25;
      } else if(windowInnerWidth > 428) {
          this.widthValue = false;
          initialGridView = 'two';
          initialWidth = 50;
      } else {
          this.widthValue = false;
          initialGridView = 'one';
          initialWidth = 100;
      }

      this.gridView = initialGridView;
      this.$emit('grid-changer', initialWidth);

    },
})
</script>