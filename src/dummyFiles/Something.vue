<template>
  <div class="announcement-carousel-viewport w-full overflow-hidden">
    <div
      ref="sliderRef"
      class="announcement-carousel-slider flex"
      :class="sliderClasses"
      :style="sliderStyle"
      @transitionend="handleTransitionEnd"
    >
      <div
        v-for="(item, index) in slidesToDisplay"
        :key="index"
        class="announcement-carousel-slide h-12 w-full shrink-0 flex items-center justify-center"
        :class="item.bgClass"
      >
        <span :class="item.spanClass">
          <p>
            <a :href="item.link" :title="item.link" :class="item.textClass">
              {{ item.text }}
            </a>
          </p>
        </span>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

// Define the shape of our announcement item
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
  data() {
    return {
      // 1. The list of your actual announcements
      announcements: [
        {
          id: 1,
          text: 'NEW IN: FIREFLY',
          link: 'https://www.nicobar.com/collections/firefly',
          bgClass: 'bg-[#af041b]', // Tailwind arbitrary value for the exact red
          textClass: 'text-white',
          spanClass: 'data-text',
        },
        {
          id: 2,
          text: 'REVISED GST RATES EFFECTIVE FROM 22.09.2025',
          link: 'https://www.nicobar.com/pages/terms-conditions',
          bgClass: 'bg-black',
          textClass: 'text-white',
          spanClass: 'data-text-secondary',
        },
        // ...add more slides here
      ] as Announcement[],

      // 2. State properties
      currentIndex: 0,
      isTransitioning: true, // Controls if the CSS transition is active
      intervalId: null as number | null, // To store our setInterval
    };
  },

  computed: {
    // 3. Creates the array with the [Slide 1, Slide 2, Slide 1 (Clone)] structure
    slidesToDisplay(): Announcement[] {
      if (this.announcements.length === 0) {
        return [];
      }
      // Return the original list + a clone of the first item at the end
      return [...this.announcements, this.announcements[0]];
    },

    // 4. Reactively calculates the transform style
    sliderStyle(): Record<string, string> {
      return {
        transform: `translateX(-${this.currentIndex * 100}%)`,
      };
    },

    // 5. Reactively calculates the transition classes
    sliderClasses(): string {
      if (this.isTransitioning) {
        // Apply Tailwind classes for a smooth transition
        return 'transition-transform duration-500 ease-in-out';
      }
      // Apply Tailwind's class for no transition (for the instant jump)
      return 'transition-none';
    },
  },

  methods: {
    // 6. The auto-play logic
    startCarousel() {
      // Clear any existing interval
      if (this.intervalId) clearInterval(this.intervalId);

      this.intervalId = window.setInterval(() => {
        this.goToSlide(this.currentIndex + 1);
      }, 3000); // 3-second delay
    },

    // 7. Moves to the next slide
    goToSlide(index: number) {
      // Always make sure transitions are ON when we move to a new slide
      this.isTransitioning = true;
      this.currentIndex = index;
    },

    // 8. The core logic for the infinite loop
    handleTransitionEnd() {
      // Check if we are on the *last* slide (the clone)
      if (this.currentIndex === this.announcements.length) {
        
        // 1. Turn off transitions
        this.isTransitioning = false;
        
        // 2. Instantly jump back to the REAL first slide (index 0)
        this.currentIndex = 0;
      }
    },
  },

  mounted() {
    // 9. Start the carousel when the component is ready
    if (this.announcements.length > 1) {
      this.startCarousel();
    }
  },

  beforeUnmount() {
    // 10. Clean up the interval when the component is destroyed
    if (this.intervalId) {
      clearInterval(this.intervalId);
    }
  },
});
</script>

<style scoped>
/* You can add any styles here that you need.
  For example, the data-text styles from your original code.
*/
.data-text,
.data-text-secondary {
  /* Your custom styles */
  font-size: 14px;
}

/* This ensures the links inside the slider
  get the text color we defined in our data.
*/
a.text-white {
  color: #ffffff;
}
</style>