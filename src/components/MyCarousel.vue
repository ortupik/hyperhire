<template>
  <q-carousel
    ref="carousel"
    v-model="slideIndex"
    :autoplay-interval="5000"
    swipeable
    animated
    control-color="white"
    infinite
    padding
    arrows
    class="transparent-bg rounded-borders"
    @input="handleSlide"
  >
    <q-carousel-slide 
      v-for="(slideContent, index) in slides" 
      :key="index" 
      :name="index"
    >
      <div class="row ">
        <MyCard 
          v-for="(card, i) in slideContent.cards" 
          :key="i" 
          :card="card" 
          :position="i"
        />
      </div>
    </q-carousel-slide>
  </q-carousel>

  <q-tooltip
    v-model="showTooltip"  
    transition-show="fade" 
    transition-hide="fade"
    anchor="top middle"
    self="top middle"
    :offset="[0, 25]"
    class="tooltip-content"
  >
    <div class="row items-center">
      <img src="dollar.png" alt="Icon" class="tooltip-icon q-mr-sm" />
      <div class="tooltip-text text-caption">월 {{randomFig}} 만원</div>
    </div>
  </q-tooltip>
</template>

<script>
import { ref, onMounted, onBeforeUnmount, computed } from 'vue';
import MyCard from 'components/MyCard.vue';

export default {
  components: {
    MyCard
  },
  setup() {
    const slideIndex = ref(0);
    const showTooltip = ref(true);  // Start with the tooltip hidden
    const tooltipTimeout = ref(null);
	let randomFig = ref(100)

    const slides = [
      {
        cards: [
          { 
            imageSrc: "profile.png", 
            name: "John Doe", 
            title: "Web Developer 5y+", 
            skills: ["Web Design", "CSS3", "JavaScript"] 
          }
        ]
      },
      {
        cards: [
          { 
            imageSrc: "profile.png", 
            name: "Jane Smith", 
            title: "UX/UI Designer 3y+", 
            skills: ["Figma Design", "Adobe XD", "User Research"] 
          }
        ]
      },
      {
        cards: [
          { 
            imageSrc: "profile.png", 
            name: "Alex Johnson", 
            title: "Data Scientist 7y+", 
            skills: ["Python", "Data Analysis", "Machine Learning"] 
          }
        ]
      },
      {
        cards: [
          { 
            imageSrc: "profile.png", 
            name: "Emily Davis", 
            title: "Marketing Specialist 4y+", 
            skills: ["Artificial Intelligence", "JavaScript", "Content Marketing"] 
          }
        ]
      }
    ];

    const currentSlideContent = computed(() => slides[slideIndex.value]);

    function handleSlide(newIndex) {
      slideIndex.value = newIndex;
	  randomFig.value = Math.floor(Math.random()*1000,2)
      // Clear any existing timeout
      clearTimeout(tooltipTimeout.value);

      // Show the tooltip
      showTooltip.value = true;
      // Set new timeout to hide the tooltip
      tooltipTimeout.value = setTimeout(() => {
        showTooltip.value = false;
      }, 2000); // Tooltip will be visible for 2 seconds
    }

    onMounted(() => {
      const timer = setInterval(() => {
        slideIndex.value = (slideIndex.value + 1) % slides.length;
		handleSlide(slideIndex.value);
      }, 5000);
      onBeforeUnmount(() => clearInterval(timer));
    });

    return { randomFig, slideIndex, showTooltip, currentSlideContent, slides, handleSlide };
  }
};
</script>
<style lang="scss" >

.q-carousel{
  height:auto;
  width:100%;
  padding: 0px;
}
q-carousel__slide{
  padding: 0px;
  background: red;
  margin: 0px;
}
.tooltip-content {
  background-color: rgba(255, 255, 255, 0.95); 
   color: #00c595;
  padding: 8px;
  border-radius: 4px;
  font-size: 14px;
}
.tooltip-icon{
    height: 19px;
    width: 19px; 
    object-fit: contain; 
}
tooltip-text{
font-size:19px;
font-weight:900;
}
</style>
