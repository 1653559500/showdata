<template>
    <div class="warningmes">
      <p class="title">告警信息展示</p>
        <div id="box">
          <ul class="list" id="ul1">
            <li class="list-li" v-for="(warning, index) in warnings">
              <img src="../../images/贴图/`DZD{9Y9$@9NB%L$F{XA2XD.png" alt="">
              <span class="span1">{{warning.name}}</span>
              <span class="span2">{{warning.status}}</span>
              <span class="last">{{warning.time}}</span>
            </li>
          </ul>
          <ul id="ul2" class="list"></ul>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Warningmes",
        data() {
            return {
              warnings: [
                {
                  src: '../../images/贴图/`DZD{9Y9$@9NB%L$F{XA2XD.png',
                  name: '储物柜1烟感传感器',
                  status: '设备离线：设备状态异常',
                  time: '2018年1月30日 13:30'
                },
                {
                  src: '../../images/贴图/`DZD{9Y9$@9NB%L$F{XA2XD.png',
                  name: '储物柜2温湿度设备',
                  status: '温度异常：数值高于20摄氏度',
                  time: '2018年1月30日 13:30'
                },
                {
                  src: '../../images/贴图/`DZD{9Y9$@9NB%L$F{XA2XD.png',
                  name: '储物柜3温湿度设备',
                  status: '设备离线：设备状态异常',
                  time: '2018年1月30日 13:30'
                },
                {
                  src: '../../images/贴图/`DZD{9Y9$@9NB%L$F{XA2XD.png',
                  name: '储物柜4烟感传感器',
                  status: '烟感异常：有烟雾',
                  time: '2018年1月30日 13:30'
                },
                {
                  src: '../../images/贴图/`DZD{9Y9$@9NB%L$F{XA2XD.png',
                  name: '储物柜5烟感传感器',
                  status: '烟感异常：有烟雾',
                  time: '2018年1月30日 13:30'
                },
                {
                  src: '../../images/贴图/`DZD{9Y9$@9NB%L$F{XA2XD.png',
                  name: '储物柜6烟感传感器',
                  status: '烟感异常：有烟雾',
                  time: '2018年1月30日 13:30'
                }
              ]
            }
        },
        mounted() {
          window.onload = roll(50);

          function roll(t) {
            let ul1 = document.getElementById("ul1");
            let ul2 = document.getElementById("ul2");
            let box = document.getElementById("box");
            ul2.innerHTML = ul1.innerHTML;
            box.scrollTop = 0;
            let timer = setInterval(rollStart, t);
            box.onmouseover = function () {
              clearInterval(timer)
            }
            box.onmouseout = function () {
              timer = setInterval(rollStart, t);
            }
          }

          function rollStart() {
            if (box.scrollTop >= ul1.scrollHeight) {
              box.scrollTop = 0;
            } else {
              box.scrollTop++;
            }
          }
        }
    }
</script>

<style scoped lang="stylus">
  #box
    height 270px
    overflow hidden
.warningmes
  position absolute
  left 1232px
  top 694px
  background linear-gradient(90deg, #1e1758 5%, #090732);
  border-radius:8px;
  width:660px;
  height:358px;
  .title
    margin 20px 0 24px 24px
    font-size:18px;
    color:#ffffff;
    text-align:left;
    line-height:28px;
    letter-spacing: 2px;
  .list
    margin-left 16px
    width 645px
    .list-li
      position relative
      width 100%
      height 55px
      line-height 55px
      margin-top 11px
      background-image:linear-gradient(90deg, #263a66 5%, #090732 98%);
      font-size 16px
      color #fff
      img
        position absolute
        top 16px
        left 8px
        width 26px
        height 26px
      span
        position absolute
      .span1
        left 44px
      .span2
        left 238px
      .last
        opacity 0.5
        left 466px
</style>
