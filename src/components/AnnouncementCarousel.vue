<template>
        <!-- Announcement bar starts -->
    <div class="announcement-carousel-viewport w-full overflow-hidden">
        <div 
           class="announcement-carosel-slider flex"
           :class="sliderClasses"
           :style="sliderStyle"
           @transitionend="handleTransition"
        >
        <!-- item and index fetched from Announcements -->
          <div 
            v-for="item in slidesToDisplay"
            :key="item.id"
            class="announcement-carosel-slider h-7 w-full shrink-0 flex items-center justify-center"
            :class="item.bgClass"
          >
          <!-- fetching from the iterable item in slidesToDisplay -->
            <span :class="item.spanClass">
              <p>
                <a :href="item.link" :title = "item.textClass"> {{ item.text }} </a>
              </p>
            </span>
          </div>
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
                bgClass: 'bg-black', // black
                textClass: 'text-white',
                spanClass: 'data-text-secondary',
              } as Announcement,
            ] as Announcement[],

        currentIndex: 0,
        isTransitioning: true,
        intervalId: null as number | null,
        }
    },

    mounted(){
        this.startCarousel();
        // as there is no need for a condition as it will always be as true as no. of banner is always > 1
    },

    computed: {
        slidesToDisplay(): Announcement[] {

            return [this.announcements[0]!, this.announcements[1]!,this.announcements[0]!]
        },

        sliderStyle(): Record<string, string> {
          return {
            // transition using index 100% -> 200%
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
            this.intervalId = window.setInterval(()=> {
                this.goToSlide(this.currentIndex + 1)
            }, 3000)
        },

        goToSlide(index: number){
            this.isTransitioning = true;
            this.currentIndex = index;
        },

        // infinity looping logic moving from 2 to 1[clone] -> 1
        handleTransition(){
            if(this.currentIndex === this.announcements.length){
              // pause transition and flip to 1
                this.isTransitioning = false;
                this.currentIndex = 0;
            }
        },
    },
})

</script>

<style scoped>

.data-text, .data-text-secondary {
  font-size: 14px;
}

a {
  color: #ffffff;
  text-decoration: underline;
}
</style>