<template>
  <div>
    <div class="overlay w-full h-full bg-[#00000080] fixed top-0 bottom-0 z-10 " @click="closeFilterBar"></div>
      <div class="product-filter-sidebar fixed top-0 right-0 h-screen bg-white w-[375px] px-5 py-7.5 z-11">
        <div class="filter-bar-header mb-1.75 text-[14px] uppercase text-[#5b6670] font-medium ml-[-3px]">
          Express Delivery
        </div>
        <div class="filter-desc font-light text-[11px] mb-3.75 pb-3 ml-[-3px]">
          Enter your PIN Code 
        </div>
        <div class=" overflow-y-auto h-150">
          <div>
            <div class="filter-header flex p-3 border-t-[#ebedf1] border-t border-solid border-b-[#ebedf1] border-b">
              <div class="pr-3 flex items-center justify-center font-bold text-[#5b6670] h-5">+</div>
              <h3 class="filter-title uppercase text-[#5b6670] cursor-pointer font-bold text-[14px]">Size</h3>
            </div>

            <div class="filter-options-list flex">
              <ul class="size-options flex flex-wrap">
                <li class="filter-option-item ">
                  <label for="Filter-Size-XS" class="facet-checkbox-label text-[10px]">
                    <input type="checkbox" name="filter.v.option.size" value="XS" id="Filter-Size-XS" class="size-checkbox">
                    <span class="filter-item-value pr-2">XS</span>
                    <span class="filter-item-count">(13)</span>
                  </label>
                </li>

                <li class="filter-option-item">
                  <label for="Filter-Size-S" class="facet-checkbox-label text-[10px]">
                    <input type="checkbox" name="filter.v.option.size" value="S" id="Filter-Size-S" class="size-checkbox">
                    <span class="filter-item-value pr-2">S</span>
                    <span class="filter-item-count">(209)</span>
                  </label>
                </li>

                <li class="filter-option-item">
                  <label for="Filter-Size-M" class="facet-checkbox-label text-[10px]">
                    <input type="checkbox" name="filter.v.option.size" value="M" id="Filter-Size-M" class="size-checkbox">
                    <span class="filter-item-value pr-2">M</span>
                    <span class="filter-item-count">(170)</span>
                  </label>
                </li>

                <li class="filter-option-item   ">
                  <label for="Filter-Size-L" class="facet-checkbox-label text-[10px]">
                    <input type="checkbox" name="filter.v.option.size" value="L" id="Filter-Size-L" class="size-checkbox">
                    <span class="filter-item-value pr-2">L</span>
                    <span class="filter-item-count">(184)</span>
                  </label>
                </li>

                <li class="filter-option-item   ">
                  <label for="Filter-Size-XL" class="facet-checkbox-label text-[10px]">
                    <input type="checkbox" name="filter.v.option.size" value="XL" id="Filter-Size-XL" class="size-checkbox">
                    <span class="filter-item-value pr-2">XL</span>
                    <span class="filter-item-count">(182)</span>
                  </label>
                </li>
                
                <li class="filter-option-item   ">
                  <label for="Filter-Size-2XL" class="facet-checkbox-label text-[10px]">
                    <input type="checkbox" name="filter.v.option.size" value="2XL" id="Filter-Size-2XL" class="size-checkbox">
                    <span class="filter-item-value pr-2">2XL</span>
                    <span class="filter-item-count">(176)</span>
                  </label>
                </li>

                <li class="filter-option-item   ">
                  <label for="Filter-Size-3XL" class="facet-checkbox-label text-[10px]">
                    <input type="checkbox" name="filter.v.option.size" value="3XL" id="Filter-Size-3XL" class="size-checkbox">
                    <span class="filter-item-value pr-2">3XL</span>
                    <span class="filter-item-count">(225)</span>
                  </label>
                </li>
                
                <li class="filter-option-item   ">
                  <label for="Filter-Size-32" class="facet-checkbox-label text-[10px]">
                    <input type="checkbox" name="filter.v.option.size" value="32" id="Filter-Size-32" class="size-checkbox">
                    <span class="filter-item-value pr-2">32</span>
                    <span class="filter-item-count">(43)</span>
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
          <button class="apply-filter-btn inline-flex flex-[50%] py-2 px-6 border-2 border-solid border-[#dfe1e3] rounded-full justify-center items-center text-[10px]">See items</button>
        </div>
      </div>
      </div>
  </div>
  
</template>

<script lang="ts">
import { defineComponent } from "vue";

// interface subCategory {
//   label: string,
//   count: number,
// }
// interface ProductCategory {
//   categoryId: string,
//   productCategoryName: string;
//   isProductCategoryActive: boolean;
//   categories: subCategory[],
// }

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
          // filterCategory: 
          // [
          //       {
          //           categoryId: 'C001',
          //           productCategoryName: 'Pattern',
          //           isProductCategoryActive: false,
          //           categories: [
          //               { label: 'solid', count: 160 },
          //               { label: 'printed', count: 106 },
          //               { label: 'checks & stripes', count: 37 },
          //               { label: 'embroidered', count: 26 },
          //               { label: 'colorblock', count: 4 },
          //               { label: 'handloom', count: 2 },
          //               { label: 'selvedge', count: 1 },
          //           ],
          //       },
          //       {
          //           categoryId: 'C002',
          //           productCategoryName: 'Size',
          //           isProductCategoryActive: false,
          //           categories: [
          //               { label: '3xl', count: 222 },
          //               { label: 's', count: 209 },
          //               { label: 'l', count: 182 },
          //               { label: 'xl', count: 182 },
          //               { label: '2xl', count: 175 },
          //               { label: 'm', count: 168 },
          //               { label: '30', count: 44 },
          //               { label: '32', count: 42 },
          //               { label: '36', count: 37 },
          //               { label: '34', count: 36 },
          //               { label: '28', count: 28 },
          //               { label: '38', count: 22 },
          //               { label: 'xs', count: 12 },
          //               { label: '33 x 33 cm', count: 5 },
          //               { label: '40', count: 4 },
          //               { label: '2 cm', count: 2 },
          //               { label: '26', count: 2 },
          //               { label: 'l-xl', count: 2 },
          //               { label: '2xl-3xl', count: 1 },
          //               { label: '3 x 6 cm', count: 1 },
          //               { label: '6 x 6.5 cm', count: 1 },
          //               { label: 's-m', count: 1 },
          //           ],
          //       },
          //       {
          //           categoryId: 'C003',
          //           productCategoryName: 'Colour',
          //           isProductCategoryActive: false,
          //           categories: [
          //               { label: 'white', count: 49 },
          //               { label: 'black', count: 41 },
          //               { label: 'navy blue', count: 35 },
          //               { label: 'blue', count: 30 },
          //               { label: 'green', count: 28 },
          //               { label: 'ivory', count: 24 },
          //               { label: 'pink', count: 19 },
          //               { label: 'grey', count: 18 },
          //               { label: 'yellow', count: 18 },
          //               { label: 'red', count: 16 },
          //               { label: 'navy', count: 15 },
          //               { label: 'charcoal', count: 13 },
          //               { label: 'beige', count: 12 },
          //               { label: 'denim blue', count: 7 },
          //               { label: 'multi', count: 6 },
          //               { label: 'gold', count: 5 },
          //               { label: 'purple', count: 5 },
          //               { label: 'teal', count: 5 },
          //               { label: 'brown', count: 4 },
          //               { label: 'mustard', count: 4 },
          //               { label: 'lime', count: 2 },
          //               { label: 'olive', count: 2 },
          //               { label: 'magenta', count: 1 },
          //           ],
          //       },
          //       {
          //           categoryId: 'C004',
          //           productCategoryName: 'Material',
          //           isProductCategoryActive: false,
          //           categories: [
          //               { label: 'cotton', count: 92 },
          //               { label: 'linen blend', count: 88 },
          //               { label: 'organic cotton', count: 67 },
          //               { label: 'silk blend', count: 38 },
          //               { label: 'cotton blend', count: 28 },
          //               { label: 'linen', count: 24 },
          //               { label: 'supima cotton', count: 12 },
          //               { label: 'cupro modal', count: 11 },
          //               { label: 'denim', count: 8 },
          //               { label: 'brass', count: 3 },
          //               { label: 'aluminium', count: 1 },
          //               { label: 'cotton elastane', count: 1 },
          //               { label: 'cotton lycocell', count: 1 },
          //               { label: 'lycocell', count: 1 },
          //               { label: 'viscose spandex', count: 1 },
          //           ],
          //       },
          //       {
          //           categoryId: 'C005',
          //           productCategoryName: 'Topwear Fit',
          //           isProductCategoryActive: false,
          //           categories: [
          //               { label: 'classic', count: 117 },
          //               { label: 'regular', count: 64 },
          //               { label: 'slim', count: 64 },
          //               { label: 'relaxed', count: 5 },
          //               { label: 'loose', count: 2 },
          //               { label: 'trim', count: 2 },
          //           ],
          //       },
          //       {
          //           categoryId: 'C006',
          //           productCategoryName: 'Bottomwear Fit',
          //           isProductCategoryActive: false,
          //           categories: [
          //               { label: 'classic', count: 22 },
          //               { label: 'regular', count: 12 },
          //               { label: 'comfy slim', count: 5 },
          //               { label: 'loose', count: 2 },
          //               { label: 'slim', count: 1 },
          //           ],
          //       },
          //       {
          //           categoryId: 'C007',
          //           productCategoryName: 'Length',
          //           isProductCategoryActive: false,
          //           categories: [
          //               { label: 'short length', count: 119 },
          //               { label: 'long length', count: 116 },
          //               { label: 'mid length', count: 33 },
          //           ],
          //       },

          //       {
          //           categoryId: 'C008',
          //           productCategoryName: 'Sleeve',
          //           isProductCategoryActive: false,
          //           categories: [
          //               { label: 'full sleeves', count: 190 },
          //               { label: 'half sleeves', count: 67 },
          //               { label: '3/4 sleeves', count: 25 },
          //               { label: 'short sleeves', count: 2 },
          //               { label: 'full sleeveless', count: 1 },
          //           ],
          //       },
          //       {
          //           categoryId: 'C009',
          //           productCategoryName: 'Ocassion',
          //           isProductCategoryActive: false,
          //           categories: [
          //               { label: 'brunches', count: 172 },
          //               { label: 'casual', count: 159 },
          //               { label: 'travelling', count: 148 },
          //               { label: 'festive', count: 91 },
          //               { label: 'weekend party', count: 66 },
          //               { label: 'workwear', count: 44 },
          //               { label: 'color block', count: 12 },
          //               { label: 'athleisure', count: 5 },
          //           ],
          //       },

          //       {
          //           categoryId: 'C010',
          //           productCategoryName: 'Category',
          //           isProductCategoryActive: false,
          //           categories: [
          //               { label: 'men', count: 368 },
          //               { label: 'accessories', count: 6 },
          //               { label: 'house & home', count: 2 },
          //               { label: 'jewellery', count: 2 },
          //           ],
          //       },
          //       {
          //           categoryId: 'C011',
          //           productCategoryName: 'Sub Category',
          //           isProductCategoryActive: false,
          //           categories: [
          //               { label: 'shirts', count: 136 },
          //               { label: 'kurtas', count: 105 },
          //               { label: 'trousers', count: 49 },
          //               { label: 't-shirts', count: 25 },
          //               { label: 'jackets', count: 14 },
          //               { label: 'essentials', count: 9 },
          //               { label: 'sweatshirts & hoodies', count: 8 },
          //               { label: 'decor', count: 2 },
          //               { label: 'cufflinks', count: 1 },
          //               { label: 'pins & brooches', count: 1 },
          //           ],
          //       },
          //   ] as ProductCategory[],
          }
        },
    emits: ['close-filter-bar'],
    methods: {
      closeFilterBar(){
        this.$emit('close-filter-bar')
      }
    }
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