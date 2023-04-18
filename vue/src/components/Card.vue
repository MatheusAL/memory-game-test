<template>
    <div v-if="card.isVisible" class="card px-3 py-3 justify-content-center align-items-center" @click="clickedCard(card.id)">
      <!-- Card content here -->
      <span>Card ID: {{ card.id }}</span>
      <span>Card name: {{ card.name }}</span>
    </div>
    <div v-else class="card card-visible px-3 py-3" @click="clickedCard(card.id)" />

  </template>
  
<script>
export default {
  name: 'Card',
  props: {
    card: Object,
    /* Card properties here */
  },
  methods: {
    /* Card methods here */
    clickedCard (id) {
      this.$emit('flippedCard', id);
    }
  }
};
</script>
  
<style scoped>
/* Card styles here */
  .card {
    background-color: grey;
    transition: transform 0.3s ease;
  }
  .card-visible {
    background-color: #33ab68;
  }
  .card:hover {
    transform: scale(1.1);
  }
</style>
