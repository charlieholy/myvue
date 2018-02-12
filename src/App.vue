<template>
  <div id="firstcomponent">
    <h1>I am a componen23.</h1>

    <ZLine></ZLine>
    <a> written by {{ author }} </a>
    <KLine></KLine>
  </div>
</template>

<script type="text/javascript">
  import ZLine from './App2.vue'
  import KLine from './AppKline.vue'
  export default {
    data () {
      return {
        author: "Jinkey"
      }
    },
    components:{
      ZLine,
      KLine
    }
  }
</script>

<style>

</style>
