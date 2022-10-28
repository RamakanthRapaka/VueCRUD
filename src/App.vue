<template>
       <SpinNer></SpinNer>
       <nav-bar></nav-bar>
       <router-view></router-view>
</template>

<script>
import NavBar from './components/NavBar.vue'
import SpinNer from './components/Spinner.vue'
export default{
  components: { NavBar, SpinNer },
       name : 'App'
}
</script>

<style>
</style>
