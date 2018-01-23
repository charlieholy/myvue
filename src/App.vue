<template>
  <div id="firstcomponent">
    <h1>I am a componen.</h1>
    <a> written by {{ author }} </a>
    <ZLine></ZLine>
  </div>
</template>

<script type="text/javascript">
  import ZLine from './App2.vue'
  export default {
    data () {
      return {
        author: "Jinkey"
      }
    },
    components:{
      ZLine
    }
  }
</script>

<style>

</style>
