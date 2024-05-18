<template>
  <q-card :class="cardClass">
    <q-card-section class="column no-wrap flex-center">
      <q-icon :name="card.icon" color="primary" size="56px"></q-icon>
      <div class="q-mt-md text-center">
        {{ card.content }}
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
    cardClass() {
      return {
        'my-card': true,
        'center-slide': this.position === 1,
        'left-slide': this.position === 0,
        'right-slide': this.position === 2
      };
    }
  }
};
</script>

<style scoped lang="scss">
.my-card {
  width: 100%;
  max-width: 250px;
  transition: transform 0.5s ease, opacity 0.5s ease;

  &.left-slide {
    transform: translateX(20%) scale(0.9);
    z-index: 1;
    opacity: 0.6;
  }

  &.right-slide {
    transform: translateX(-20%) scale(0.9);
    z-index: 1;
    opacity: 0.6;
  }

  &.center-slide {
    transform: translateX(0) scale(1);
    z-index: 2;
    opacity: 1;
  }
}
</style>
