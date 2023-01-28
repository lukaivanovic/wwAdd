<script>
  export default {
    data() {
      return {
        isOpened: false,
        tab: "Layouts"
      }
    },
  }
</script>

<script setup>
import Navigation from "./components/Navigation.vue"
import AddPanel from "./components/AddPanel.vue"
</script>

<template>
  <header>
    <link rel="preconnect" href="https://rsms.me/">
    <link rel="stylesheet" href="https://rsms.me/inter/inter.css">  
  </header>
  <div> {{count}} </div>
  <main>
    <AddPanel />
    <Navigation />
  </main>
</template>

<style scoped>
</style>
