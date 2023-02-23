<template>
  <div id='app'>
    <ToDoApp></ToDoApp>
    <Footer></Footer>
  </div>
</template>

<script>
import ToDoApp from './components/TodoApp.vue';
import Footer from './components/Footer.vue';

export default { components: { ToDoApp, Footer } }

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Mulish:wght@400;500;600;700;800&family=Space+Mono:wght@400;700&display=swap');

</style>