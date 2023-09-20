<template>
    <footer>
        <p>&copy; {{ currentYear }} K13 Mester</p>
    </footer>
</template>

<style scoped>
    footer{
        text-align: center;
        background: #ccc;
    }
</style>

<script>
export default {
    data() {
    return {
      currentYear: new Date().getFullYear(),
      showScrollButton: false,
    };
  }
}

</script>