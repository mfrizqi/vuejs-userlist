<template>
  <div id="app"> 
    <UserPage/>
  </div>
</template>

<script>

import UserPage from './components/UserPage'

export default {
  name: 'App',
  components: {
    UserPage,
  },
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
