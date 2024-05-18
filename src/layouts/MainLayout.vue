<template>
  <q-layout view="lHh Lpr lFf" >
   <div class="jumbotron">
    <HeaderTop class="transparent-bg" />
    <JumboTop class="transparent-bg  " /> 
  	</div>
    <q-page-container>
      <router-view />
    </q-page-container>
	<footer class="sticky-footer q-pa-sm text-center bg-grey-2"> 
      &copy; 2023 Hyperhire 
    </footer>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'
import HeaderTop from 'components/HeaderTop.vue'
import JumboTop from 'components/JumboTop.vue'
  
defineOptions({
  name: 'MainLayout'
})

</script>

<style lang="scss">
.jumbotron {
  background-size: cover;
  background-position: center;
  min-height: 500px;
  color: white; // Set text color to white for better contrast
  background: linear-gradient(180deg, #30a192 0%, #3a9ad9 100%)}


.transparent-bg {
  background: transparent !important; // Override default background
}


.sticky-footer {
  position: sticky;
  bottom: 0;
  width: 100%;
  z-index: 10;
  font-weight: bold;    /* Make the text bold */
  font-size: 1.0rem;   /* Increase font size slightly */
}
</style>
