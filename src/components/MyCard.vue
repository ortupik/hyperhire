<template>
  <q-card class="my-card ">
    <q-card-section class="q-pa-none text-center">
      <q-avatar size="100px" class="q-mb-md q-mx-auto">
        <img :src="card.imageSrc" alt="Abhishek Gupta">
      </q-avatar>

      <div class="text-h5 text-weight-bold">{{ card.name }}</div>
      <div class="text-primary  text-weight-bold title" color="primary">{{ card.title }}</div>

      <q-separator spaced />
	  <div class="justify-center items-center top-skill flex">
       <div class="skill-div">{{card.skills[0]}}</div>
	   <div class="skill-div">{{card.skills[1]}}</div>
       <div class="skill-div">{{card.skills[2]}}</div>
	   </div>

    </q-card-section>
  </q-card>
</template>

<script>
export default {
  props: {
    card: Object,
    position: Number
  },
  computed: {

  }
};
</script>

<style scoped lang="scss">
.top-skill {
  margin-top: 10px;
  margin-bottom:10px;
  padding:10px;
}
.skill-div {
  border: 0.3px solid gray; 
  color: #616161; /* Dark gray text color */
  padding: 5px;
  width: fit-content; 
  border-radius: 8px; 
  margin:5px;
  text-align: center;
}

.my-card {
  width: 100%;
  transition: transform 0.5s ease, opacity 0.5s ease;
  height: 100%;
  color: darkgray;
  border-radius: 10px; 
  min-height:360px;
  
  .title{
    font-size:16px;
	margin-top: 8px;
	margin-bottom: 15px;
  }
}
.q-avatar {
  border-radius: 15px;
  overflow: hidden;
  transition: transform 0.2s ease;
  margin-top:30px;
  margin-bottom: 25px;

  &:hover {
    transform: scale(1.05);
    filter: brightness(1.1);
  }

  img {
    object-fit: cover;
  }
}

</style>
