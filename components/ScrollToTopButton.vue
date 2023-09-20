<template>
    <button v-if="showButton" class="scroll-button" @click="scrollToTop">
      <span class="arrow-up"></span>
    </button>
  </template>
  
  <script>
  export default {
    data() {
      return {
        showButton: false,
      };
    },
    methods: {
      scrollToTop() {
        window.scrollTo({
          top: 0,
          behavior: 'smooth',
        });
      },
      handleScroll() {
        this.showButton = window.scrollY > 0;
      },
    },
    mounted() {
      window.addEventListener('scroll', this.handleScroll);
    },
    beforeDestroy() {
      window.removeEventListener('scroll', this.handleScroll);
    },
  };
  </script>
  
  <style scoped>
  .scroll-button {
    position: fixed;
    bottom: 50px;
    right: 2%;
    width: 50px;
    height: 50px;
    cursor: pointer;
    background-color: #bbbbbb;
    align-items: center;
    justify-content: center;
    display: flex;
    z-index: 9999;
  }
  
  .scroll-button:hover {
    background-color: #15b1e5;
  }
  
  .arrow-up {
    display: inline-block;
    border: solid white;
    border-width: 0 3px 3px 0;
    padding: 5px;
    transform: rotate(-135deg);
    /* You can adjust the color, size, and other styles as needed */
  }
  </style>
  