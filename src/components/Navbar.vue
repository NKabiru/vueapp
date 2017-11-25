<template>
  <div class="top-bar">
    <div class="top-bar-left">
        <span><router-link :to="{name: 'Home'}" >{{ title }}</router-link></span>
        <span><router-link :to="{name: 'Employee'}">Employees</router-link></span>
        <span><router-link :to="{name: 'About'}">About</router-link></span>
    </div>
    <div class="top-bar-right">
      <ul class="menu">
        <li><input type="text" placeholder="Search"/></li>
        <li><button class="button" @click="search">Search</button></li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  data(){
      return {
          title: 'EMS'
      }
  },
    methods: {
      search(){
          console.log("Search button clicked");
      }
    }
}
</script>

<style>

</style>
