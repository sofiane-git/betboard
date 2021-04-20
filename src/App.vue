<template>

  <div id="app" class="bg-yellow-600 flex justify-center items-center h-screen sm:p-1 lg:p-2">
    <div class="relative bg-white h-full w-full overflow-y-scroll inner px-2">
      <TheHeader></TheHeader>
      <!-- <div class="flex"> -->
        <Stats></Stats>
      <!-- </div> -->
    </div>
  </div>
</template>

<script>
import Stats from './components/Stats/Stats'
import TheHeader from './components/TheHeader'
// import Bankroll from './components/Bankroll/Bankroll'

export default {
  name: 'App',
  components: {
    TheHeader,
    Stats,
    // Bankroll
  }
}
</script>

<style>
  .inner::-webkit-scrollbar {
  display: none;
  }
  .inner {
  -ms-overflow-style: none;  
  overflow: -moz-scrollbars-none; 
  scrollbar-color: rebeccapurple green;
  scrollbar-width: thin;
  }

</style>
