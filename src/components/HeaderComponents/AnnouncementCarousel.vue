<template>
        <!-- Announcement bar starts -->
    <div class="announcement-carousel-viewport w-full overflow-hidden">
        <div 
           class="announcement-carosel-slider flex"
           :class="sliderClasses"
           :style="sliderStyle"
           @transitionend="handleTransition"
        >
           <div 
              v-for="(item, index) in slidesToDisplay"
              :key="index"
              class="announcement-carosel-slider h-7 w-full shrink-0 flex items-center justify-center"
              :class="item.bgClass"
            >
               <span :class="item.spanClass">
                    <p>
                        <a :href="item.link" :title = "item.textClass" >{{ item.text }}</a>
                    </p>
               </span>
           </div>
           <!-- <div class="announcement-carosel-slider">
                <span class="data-text-secondary">
                     <p>
                        <a href="https://www.nicobar.com/pages/terms-conditions" title="https://www.nicobar.com/pages/terms-conditions">REVISED GST RATES EFFECTIVE FROM 22.09.2025</a>
                    </p>
               </span>
           </div> 
        </div> -->
    </div>
    </div>
    <!-- Announcement bar ends -->
</template>

<script lang="ts">
// imported to typescript
import { defineComponent } from 'vue';

// shape of announcement
interface Announcement {
    id: number;
    text: string;
    link: string;
    bgClass: string;
    textClass: string;
    spanClass: string;
}

export default defineComponent({
    name: 'AnnouncementCarousel',

    data(){
        return {
            announcements: [
              {
                id: 1,
                text: 'NEW IN: FIREFLY | EXPRESS DELIVERY AVAILABLE',
                link: 'https://www.nicobar.com/collections/firefly',
                bgClass: 'bg-[#af041b]', // red
                textClass: 'text-white',
                spanClass: 'data-text',
              } as Announcement,
              {
                id: 2,
                text: 'REVISED GST RATES EFFECTIVE FROM 22.09.2025',
                link: 'https://www.nicobar.com/pages/terms-conditions',
                bgClass: 'bg-black', 
                textClass: 'text-white',
                spanClass: 'data-text-secondary',
              } as Announcement,
            ] as Announcement[],

        currentIndex: 0,
        isTransitioning: true,
        intervalId: null as number | null,
        }
    },

    computed: {
        slidesToDisplay(): Announcement[] {

            return [...this.announcements, this.announcements[0]]
        },

        sliderStyle(): Record<string, string> {
          return {
            transform: `translateX(-${this.currentIndex * 100}%)`
          }
        },

        sliderClasses(): string {
            if(this.isTransitioning) return 'transition-transform duration-500 ease-in-out';

            return 'transition-none';
        }
    },

    methods: {
        startCarousel(){
            if(this.intervalId) clearInterval(this.intervalId);

            this.intervalId = window.setInterval(()=> {
                this.goToSlide(this.currentIndex + 1)
            }, 3000)
        },

        goToSlide(index: number){
            this.isTransitioning = true;
            this.currentIndex = index;
        },

        // infinity looping logic moving from 2 to 1clone -> 1
        handleTransition(){
            if(this.currentIndex === this.announcements.length){
                this.isTransitioning = false;

                this.currentIndex = 0;
            }
        },
    },

    mounted(){
        if(this.announcements.length > 1){
            this.startCarousel();
        }
    },
    beforeUnmount() {
    if (this.intervalId) {
      clearInterval(this.intervalId);
    }
  },
})

</script>

<style scoped>

.data-text {
  font-size: 10px;
}

.data-text-secondary {
  font-size: 14px;
}

a {
  color: #ffffff;
  text-decoration: underline;
}
</style>