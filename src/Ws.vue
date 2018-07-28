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
              var ping = {"cmd":"ping"}
              var ticks = { "cmd":"ticks",
                              "channel":"add",
                              "symbols":["SYS_ETH","EOS_BTC"]}
              var depth =  {"cmd":"depth","channel":"add","symbol":"EOS_ETH"}
              var allab = {"cmd":"allAB"}
              var cmd_ping = JSON.stringify(ping)
              var cmd_ticks = JSON.stringify(ticks)
              var cmd_depth = JSON.stringify(depth)
              var cmd_allab = JSON.stringify(allab)

              var keepalive = function(){
                ws.send(cmd_ping);
              }

              ws.onopen = () => {
              console.log("cmd_ping  " + cmd_ping)
              console.log("cmd_ticks  " + cmd_ticks)
                   ws.send(cmd_ping)
                   ws.send(cmd_ticks)
                   ws.send(cmd_depth)
                   ws.send(cmd_allab)
                   console.log('数据发送中...')
                   setInterval(keepalive,50000);
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
