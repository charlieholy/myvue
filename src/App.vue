<template>
  <div id="firstcomponent">
    <h1>I am a componen23.</h1>
    <a> written by {{ author }} </a>
    <Ws></Ws>
  </div>
</template>

<script type="text/javascript">
  import ZLine from './App2.vue'
  import KLine from './AppKline.vue'
  import KLine2 from './AppKline2.vue'
  import RqImage from './AppQrImage.vue'
  import Ws from './Ws.vue'
  export default {
    data () {
      return {
        author: "charlie"
      }
    },
    components:{
      ZLine,
      KLine,
      KLine2,
      RqImage,
      Ws
    }
  }
</script>

<style>

</style>
