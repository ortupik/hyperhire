<template>
  <q-layout view="lHh Lpr lFf" >
   <div class="jumbotron">
    <HeaderTop class="transparent-bg header" />
    <JumboTop class="transparent-bg main"  /> 
  	</div>
    <q-page-container class="page-body">
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
@media (min-width: 992px) {
  .header{
    padding-left:70px;
	padding-right:50px;
	padding-top: 20px;
  }
  .main {
    padding: 70px;
  }
  
}
@media (max-width: 992px) {
  .header{
    padding-left:10px;
	padding-right:10px;
	padding-top: 10px;
  }
  
}
@media (min-width: 1400px) {
.page-body{
  padding: 100px;
}
}
@media (max-width: 1400px) {
.page-body{
  padding: 50px;
}
}

.jumbotron {
  background-size: cover;
  background-position: center;
  min-height: 500px;
  color: white; // Set text color to white for better contrast
  background: linear-gradient(180deg, #2ea39b 0%, #3a9ad9 100%)}


.transparent-bg {
  background: transparent !important; // Override default background
}


.sticky-footer {
  bottom: 0;
  width: 100%;
  z-index: 10;
  font-weight: bold;    /* Make the text bold */
  font-size: 1.0rem;   /* Increase font size slightly */
}
</style>
