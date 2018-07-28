<template>
  <div class="qart">
    <div id="qrcode" ref="qrcode">
    </div>
    <input type="text" id="getval" value="" placeholder="修改这个值改变二维码">
  </div>
</template>

<script>
require("./common/qrcode")
  export default {
    components: {

    },
    data() {
      return {
        i:false
      }
    },
    created() {

    },
    mounted() {
      this.websocket()
    },

    methods: {

       websocket () {
              let ws = new WebSocket('ws://47.75.144.95:12389')
              let pako = require('pako')
              var cmd = {"cmd":"ping"}
              ws.onopen = () => {
              var s = JSON.stringify(cmd)
              console.log("cmd  " + s)
                   ws.send( s)
                   console.log('数据发送中...')
               }
               ws.onmessage = evt => {
                  var msg = evt.data
                  console.log("res " + msg);
                  var b64 = new Buffer(msg, 'base64')
                  var json = pako.inflate(new Uint8Array(b64), {to: 'string'});
                  var sss = decodeURIComponent(json)
                  console.log("ressss " + sss)
               }
               ws.onclose = function () {
                 console.log('连接已关闭...')
               }
                // 组件销毁时调用，中断websocket链接
               this.over = () => {
                console.log("close")
                 ws.close()
               }
         }

    }

  }

</script>

<style>
  #qrcode{
    height: 200px;
    width: 200px;
    margin: auto;
  }
</style>
