<template>
    <button class="reset-button btn-lg" @click="reset">
      <!-- Reset button content here -->
      Reset Game!
    </button>
</template>
  
<script>
export default {
  name: 'ResetButton',
  methods: {
    reset() {
      /* Reset logic here */
    }
  }
};
</script>

<style scoped>
/* Reset button styles here */
  .reset-button {
    background-color: #33ab68;
    border-radius: 50px;
    text-align: center;
    width: 200px;
    font-weight: bold;
  }
</style>
  