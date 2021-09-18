<template>
    <div>
        <the-header></the-header>
        <the-calendar></the-calendar>
    </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import TheCalendar from './components/TheCalendar.vue'
export default {
  components: {TheHeader, TheCalendar}
  
}
</script>


<style>
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;

  }
</style>