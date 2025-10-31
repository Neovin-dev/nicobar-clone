<template>
<div class="collectionToolbar py-0.5 px-10 flex justify-between pt-4 sticky top-0 bg-white z-5 w-full">
    <div class="collectionToobarView flex flex-row py-5">
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
      <span class="productCount text-[12px] text-[#9ea5ad] pl-2">
        371 Items
      </span>
    </div>
    <div class="collectionToolbarFilterSort flex h-10 align-middle">
      <div class="collectionToolbarSort inline-flex py-2 px-4 border-2 border-solid border-[#dfe1e3] rounded-full justify-center items-center relative">
        <div @click="sortState" class="sort-by-select-header flex text-center text-[10px] cursor-pointer">
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
        <ul v-if="sortVisible" @click="handleSort" class="min-w-[270px] sort-by-data absolute top-12 bg-white text-left text-[10px] text-[#1a1f29] z-9 w-full float-left shadow-[1px_1px_4px_#7070704d] m-0 -left-10 cursor-pointer">
              <li value="created-descending" class="data first-child tracking-[0] font-normal px-5 py-[15px] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="3" data-value="created-descending"><span>What’s New</span></li>
              <li value="manual" class="data is-selected tracking-[0] font-normal px-5 py-[15px] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="0" data-value="manual"><span>Featured</span></li>
              <li value="price-ascending" class="data tracking-[0] font-normal px-5 py-[15px] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="1" data-value="price-ascending"><span>Price - low to high</span></li>
              <li value="price-descending" class="data tracking-[0] font-normal px-5 py-[15px] border-t-[rgba(182,184,187,0.2)] border-t border-solid hover:bg-[#ebedf1]" data-index="2" data-value="price-descending"><span>Price - high to low</span></li>
        </ul>
      
      </div>
      <div class="filter-container flex ml-2.5 " @click="filterState" >
        <button class="filter-bar inline-flex py-2 px-6 border-2 border-solid border-[#dfe1e3] rounded-full justify-center items-center text-[10px] cursor-pointer">
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
</template>

<script lang="ts">
import { defineComponent } from "vue";
type GridView = 'two' | 'four';
export default defineComponent ({
    name: 'CollectionToolbar',
    data(): {gridView : GridView} {
      return {
        gridView: 'four',
      };
    },
    emits: ['handle-sort', 'filter-state', 'sort-state'],
    props: {
      sortVisible: {
        type: Boolean,
        required: true,
      }
    },
    methods: {
      handleSort(event: Event){
        const targetli = (event.target as HTMLElement).closest('li');
        if(targetli){
          const selectedValue = targetli.getAttribute('value');
          this.$emit('handle-sort', selectedValue);
        }
      },
      gridChangerfour(){
        this.gridView = 'four';
      },
      gridChangertwo(){
        this.gridView = 'two';
      },
      filterState() {
        this.$emit('filter-state')
        console.log('filter-state-triggered');
      },
      sortState(){
        this.$emit('sort-state')
      }
    }
})
</script>