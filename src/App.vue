<template>
  <div id="firstcomponent">
    <h1>I am a componen.</h1>
    <a> written by {{ author }} </a>
    <App2></App2>
  </div>
</template>

<script type="text/javascript">
  import App2 from './App2.vue'
  export default {
    data () {
      return {
        author: "Jinkey"
      }
    },
    components:{
      App2
    }
  }
</script>

<style>

</style>
