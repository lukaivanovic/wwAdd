<script>
  export default {
    data() {
      return {
        isOpened: false,
        tab: "Layouts"
      }
    },
    methods: {
      openPanel(){
        this.isOpened = true;
      },
      closePanel(){
        this.isOpened = false;
      }
    }
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

  <main>
    <AddPanel v-if="isOpened" @close-panel="closePanel"/>
    <Navigation @open-panel="openPanel"/>
  </main>
</template>

<style scoped>
</style>
