<template>
  <div id="app">
    <navbar></navbar>
      <div class="grid-container">
        <router-view/>
      </div>
    <bottom-bar></bottom-bar>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
import BottomBar from '@/components/BottomBar.vue'

var mixin = {
    created: function(){
        console.log("Success");
    }
};
export default {
  mixins: [mixin],
  name: 'app',
  components: { Navbar, BottomBar }
}
</script>

<style>
  .grid-container{
    overflow: auto;
    height: 100vh;
    display: flex;
  }
</style>
