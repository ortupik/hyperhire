<template>

        <div class="row full-width full-height justify-center items-center transparent-bg jumbo">
          <div class="col-md-6 col-12 bg-white q-pa-lg  transparent-bg">
             <div class="text-h4 text-weight-bold fade-up">
              Finding the best foreign talent?
            </div>
            <div class="text-h6 text-weight-bold q-my-md fade-up">
              Hire remotely within a week without the hassle of HR management.
            </div>
            <div class="text-h5 que ">Need a developer?</div>
            <div class="row q-mt-lg fade-in">
              <div class="col-12 col-md-4 sum">
			    <div class=" with-top-line"></div>
                <div class="text-h6 text-weight-bold">Avg. $1,200/month</div>
                <div>Calculated based on the wages of the respective country.</div>
              </div>
              <div class="col-12 col-md-4 sum">
			    <div class=" with-top-line"></div>
                <div class="text-h6 text-weight-bold">Up to 3 replacements</div>
                <div>Don't worry if the hire doesn't work out.</div>
              </div>
              <div class="col-12 col-md-4 sum">
			    <div class=" with-top-line"></div>
                <div class="text-h6 text-weight-bold">Avg. 3 days, max 10 days</div>
                <div>Fast hiring is possible even in urgent cases.</div>
              </div>
            </div>
          </div>
          <div class="col-md-6 col-12 bg-white  transparent-bg">
		    <LargeCarousel />
          </div>
		  
		  <div class="col-12">
		    <q-carousel
				v-model="slide"
				transition-prev="slide-right"
				transition-next="slide-left"
				animated
				autoplay
				infinite
				:interval="5000" 
				swipeable
				class="carousel  hide-scrollbar"
						  >
				<q-carousel-slide :name="1" class="row no-wrap justify-start items-center q-gutter-md hide-scrollbar">
				  <q-btn 
					v-for="(item, index) in slides.slice(0, 4)" :key="index"
					flat 
					no-caps
					class="transparent-button active" 
				  >
				  <img :src="item.imgSrc" alt="Icon" class="q-mr-sm icon" />
				  <div class="label">{{ item.label }}</div>
				  </q-btn>
				</q-carousel-slide>

				<q-carousel-slide :name="2" class="row no-wrap justify-start items-center q-gutter-md hide-scrollbar">
				  <q-btn 
					v-for="(item, index) in slides.slice(1, 5)" :key="index"
					flat 
					no-caps
					class="transparent-button" 
				  >
				  <img :src="item.imgSrc" alt="Icon" class="q-mr-sm icon" />
				  <div class="label">{{ item.label }}</div>
				  </q-btn>
				</q-carousel-slide>
		</q-carousel>
		  </div>
        </div>
</template>

<script >
  import { ref } from 'vue';

  import LargeCarousel from 'components/LargeCarousel.vue'
  //import SmallCarousel from 'components/SmallCarousel.vue'


export default {
  components: {
    LargeCarousel,
	//SmallCarousel
  },
  setup() {
    return {
      slide: ref('1'), // Initial slide
      slides: [
        { imgSrc: ('1.png'), label: '해외 마케팅' },
        { imgSrc: '2.png', label: '퍼블리셔' },
        { imgSrc: '3.png', label: '캐드원(제도사)' },
        { imgSrc: '4.png', label: '해외 세일즈' },
        { imgSrc: '5.png', label: '해외 CS' },
      ],
    };
  },
  mounted() {
    // Add the active classes to trigger the transitions
    this.$nextTick(() => {
      const fadeUpElements = document.querySelectorAll('.fade-up');
      const fadeInElements = document.querySelectorAll('.fade-in');

      fadeUpElements.forEach(el => el.classList.add('fade-up-active'));
      fadeInElements.forEach(el => el.classList.add('fade-in-active'));
    });
  }
};
</script>

<style lang="scss">
.sum{
  margin-bottom:20px;
  margin-top:20px;
  padding:10px;
}
.carousel{
  background: transparent;
  height: auto;
  margin-top:30px;
  margin-bottom:30px;
}
.transparent-button {
  color: white; 
  border: none;    
  padding: 25px 25px; 
  border-radius: 8px; 
  min-width: 250px; 
   background-color: rgba(255, 255, 255, 0.15);
   
  .q-btn__content {
    align-items: center;         /* Vertically center icon and text */
    gap: 18px;                  /* Add spacing between icon and text */
	font-size:25px;
	flex-direction: row-reverse; 
  }
  .label {
    order: 1; /* Ensure label comes first */
    font-size: 25px; 
  }

  .icon {
    order: 2; /* Ensure icon comes second */
    height: 39px; /* Set the desired height */
    width: 39px; /* Set the desired width */
    object-fit: contain; /* How the image should fit inside the container */
  }
  
}

.que{
  margin-bottom: 30px;
  margin-top: 40px;
}
 .with-top-line {
    border-top: 1px solid white; /* Adjust thickness as needed */
    padding-top: 4px; 
	margin-right:10px;
  }
.fade-up {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 1500ms ease-in-out, transform 500ms ease-in-out;

  &.fade-up-active { 
    opacity: 1;
    transform: translateY(0);
  }
}
.fade-in {
  opacity: 0;
  transition: opacity 500ms ease-in;
  
  &.fade-in-active { 
    opacity: 1;
  }
}
.jumbo {
  padding: 30px;
}
/* Hide scrollbar styles */
.q-panel {
  -ms-overflow-style: none;  /* Internet Explorer 10+ */
  scrollbar-width: none;  /* Firefox */
}


</style>
