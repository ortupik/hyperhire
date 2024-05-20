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
      class="carousel-slide"
    >
      <div class="card-container">
        <MyCard 
          v-for="(card, i) in slideContent.cards" 
          :key="i" 
          :card="card" 
          :class="{'left-card': i === 0, 'center-card': i === 1, 'right-card': i === 2}"
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
    :offset="[0, 45]"
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
    const showTooltip = ref(true);
    const tooltipTimeout = ref(null);
    let randomFig = ref(100);

    const slides = [
      {
        cards: [
          { 
            imageSrc: "profile.png", 
            name: "John Doe", 
            title: "Web Developer 5y+", 
            skills: ["Web Design", "CSS3", "JavaScript"] 
          },
          { 
            imageSrc: "profile.png", 
            name: "Jane Smith", 
            title: "UX/UI Designer 3y+", 
            skills: ["Figma Design", "Adobe XD", "User Research"] 
          },
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
          },
          { 
            imageSrc: "profile.png", 
            name: "Michael Brown", 
            title: "DevOps Engineer 6y+", 
            skills: ["AWS", "Docker", "Kubernetes"] 
          },
          { 
            imageSrc: "profile.png", 
            name: "Sophia Lee", 
            title: "Product Manager 3y+", 
            skills: ["Project Management", "Agile", "Scrum"] 
          }
        ]
      }
    ];

    const currentSlideContent = computed(() => slides[slideIndex.value]);

    function handleSlide(newIndex) {
      slideIndex.value = newIndex;
      randomFig.value = Math.floor(Math.random() * 1000, 2);
      clearTimeout(tooltipTimeout.value);
      showTooltip.value = true;
      tooltipTimeout.value = setTimeout(() => {
        showTooltip.value = false;
      }, 2000);
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

<style lang="scss">
.q-carousel {
  height: auto;
  width: 100%;
  padding: 0px;
}

.carousel-slide {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0px;
  margin: 0px;
}

.card-container {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  width: 100%;
}

.MyCard {
  transition: transform 0.3s, z-index 0.3s;
  position: absolute;
}

.left-card {
  transform: translateX(50%) scale(0.85);
  z-index: 1;
  opacity: 0.8;

}

.center-card {
  transform: translateX(0);
  z-index: 2;
  width: 50%;
}

.right-card {
  transform: translateX(-50%) scale(0.85);
  z-index: 1;
  opacity: 0.8;
}

.tooltip-content {
  background-color: rgba(255, 255, 255, 0.95);
  color: #00c595;
  padding: 8px;
  border-radius: 4px;
  font-size: 14px;
}

.tooltip-icon {
  height: 19px;
  width: 19px;
  object-fit: contain;
}

.tooltip-text {
  font-size: 19px;
  font-weight: 900;
}
</style>
