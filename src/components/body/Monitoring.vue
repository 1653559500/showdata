<template>
    <div class="monitoring">
      <p class="title">厂外环境监控</p>
      <div class="data">
        <div class="data-list">
          <div class="bg-img"></div>
          <canvas class="data-chars" ref="chars1" width="104" height="54"></canvas>
          <div class="icon-img"><img src="../../images/贴图/F6287D84-A8E6-4665-ABAD-CA773B23414E@1x.png" alt=""></div>
          <p class="data-p1 temperature">{{data.temperature.init}}℃</p>
          <p class="data-title">{{data.temperature.name}}</p>
        </div>
        <div class="data-list">
          <div class="bg-img"></div>
          <canvas class="data-chars1" width="104" height="54"></canvas>
          <div class="icon-img"><img src="../../images/贴图/C9F06CF0-7207-4315-8B5D-E48E67C012B9@1x.png" alt=""></div>
          <p class="data-p1 humidity">{{data.humidity.init*100}}%</p>
          <p class="data-title">{{data.humidity.name}}</p>
        </div>
        <div class="data-list">
          <div class="bg-img"></div>
          <canvas class="data-chars2" width="104" height="54"></canvas>
          <div class="icon-img"><img src="../../images/贴图/A3CDECC5-1DAC-4A8C-B683-60E3AAAE49E8@1x.png" alt=""></div>
          <p class="data-p1 pm10">{{data.pm10.init}}μg/m³</p>
          <p class="data-title">{{data.pm10.name}}</p>
        </div>
        <div class="data-list">
          <div class="bg-img"></div>
          <canvas class="data-chars3" width="104" height="54"></canvas>
          <div class="icon-img"><img src="../../images/贴图/09EEB026-1F2A-45DA-B3DC-C0ED76CDCE9E@1x.png" alt=""></div>
          <p class="data-p1 pm2">{{data.pm2.init}}μg/m³</p>
          <p class="data-title">{{data.pm2.name}}</p>
        </div>
        <div class="data-list">
          <div class="bg-img"></div>
          <canvas class="data-chars4" width="104" height="54"></canvas>
          <div class="icon-img"><img src="../../images/贴图/9E21489B-E53D-4B16-8A44-BADA6CF4BA7A@1x.png" alt=""></div>
          <p class="data-p1 formaldehyde">{{data.formaldehyde.init}}mg/m³</p>
          <p class="data-title">{{data.formaldehyde.name}}</p>
        </div>
        <div class="data-list">
          <div class="bg-img"></div>
          <canvas class="data-chars5" width="104" height="54"></canvas>
          <div class="icon-img"><img src="../../images/贴图/D4240447-CB93-4C1A-89C5-BDD051F97E98@1x.png" alt=""></div>
          <p class="data-p1 tovc">{{data.tovc.init}}mg/m³</p>
          <p class="data-title">{{data.tovc.name}}</p>
        </div>
      </div>
    </div>
</template>

<script>
    export default {
      name: "Monitoring",
      data() {
        return {
          data: {
            temperature: {min: -10, max: 50, init: 30, name: '温度'},// 温度
            humidity: {min: 0.1, max: 0.9, init: 0.5, name: '湿度'}, // 湿度
            pm10: {min: 10, max: 100, init: 53, name: 'PM10'},
            pm2: {min: 20, max: 86, init: 37, name: 'PM2.5'},
            formaldehyde: {min: 20, max: 86, init: 23, name: '甲醛'},
            tovc: {min: 20, max: 86, init: 30, name: 'TOVC'}
          }
        }
      },
      mounted(){
        //温度比例
        let scale = (this.data.temperature.init/(this.data.temperature.max - this.data.temperature.min)).toFixed(2)
        // 湿度比例
        let humidityScale = (this.data.humidity.init/(this.data.humidity.max - this.data.humidity.min)).toFixed(2)
        // pm10
        let pm10Scale = (this.data.pm10.init/(this.data.pm10.max - this.data.pm10.min)).toFixed(2)
        // pm2.5
        let pm2Scale = (this.data.pm2.init/(this.data.pm2.max - this.data.pm2.min)).toFixed(2)
        // 甲醛
        let formaldehydeScale = (this.data.formaldehyde.init/(this.data.formaldehyde.max - this.data.formaldehyde.min)).toFixed(2)
        //tovc
        let tovcScale = (this.data.tovc.init/(this.data.tovc.max - this.data.tovc.min)).toFixed(2)

          let dataChars = document.querySelector('.data-chars')
          //按照温度比例改变canvas的width
          dataChars.width = dataChars.width * scale
          const context = dataChars.getContext('2d')
          context.lineWidth = 6;
          context.beginPath();
          context.arc(52, 50, 46, 0, 180*Math.PI/180 , true);
          context.strokeStyle = '#36d2cf';
          context.lineCap = 'round'
          context.stroke();

          // 湿度
          let dataChars1 = document.querySelector('.data-chars1')
          //按照湿度比例改变canvas的width
          dataChars1.width = dataChars1.width * humidityScale
          const context1 = dataChars1.getContext('2d')
          context1.lineWidth = 6;
          context1.beginPath();
          context1.arc(52, 50, 46, 0, 180*Math.PI/180 , true);
          context1.strokeStyle = '#c3ff58';
          context1.lineCap = 'round'
          context1.stroke();

          //  PM10 #c56cd7
          let dataChars2 = document.querySelector('.data-chars2')
          //按照湿度比例改变canvas的width
          dataChars2.width = dataChars2.width * pm10Scale
          const context2 = dataChars2.getContext('2d')
          context2.lineWidth = 6;
          context2.beginPath();
          context2.arc(52, 50, 46, 0, 180*Math.PI/180 , true);
          context2.strokeStyle = '#c56cd7';
          context2.lineCap = 'round'
          context2.stroke();

          // PM2.5 #45f1bb
          let dataChars3 = document.querySelector('.data-chars3')
          //按照湿度比例改变canvas的width
          dataChars3.width = dataChars3.width * pm2Scale
          const context3 = dataChars3.getContext('2d')
          context3.lineWidth = 6;
          context3.beginPath();
          context3.arc(52, 50, 46, 0, 180*Math.PI/180 , true);
          context3.strokeStyle = '#45f1bb';
          context3.lineCap = 'round'
          context3.stroke();

          //甲醛 #f8a640
          let dataChars4 = document.querySelector('.data-chars4')
          //按照湿度比例改变canvas的width
          dataChars4.width = dataChars4.width * formaldehydeScale
          const context4 = dataChars4.getContext('2d')
          context4.lineWidth = 6;
          context4.beginPath();
          context4.arc(52, 50, 46, 0, 180*Math.PI/180 , true);
          context4.strokeStyle = '#f8a640';
          context4.lineCap = 'round'
          context4.stroke();

          // tovc #92e88c
          let dataChars5 = document.querySelector('.data-chars5')
          //按照湿度比例改变canvas的width
          dataChars5.width = dataChars5.width * formaldehydeScale
          const context5 = dataChars5.getContext('2d')
          context5.lineWidth = 6;
          context5.beginPath();
          context5.arc(52, 50, 46, 0, 180*Math.PI/180 , true);
          context5.strokeStyle = '#92e88c';
          context5.lineCap = 'round'
          context5.stroke();

      },
    }

</script>

<style scoped lang="stylus">

  .monitoring
    position absolute
    left 700px
    top 694px
    background-image:linear-gradient(-51deg, rgba(11,15,86,0.55) 0%, rgba(9,9,57,0.31) 99%);
    border-radius:8px;
    width:504px;
    height:358px;
    font-family:PingFangSC-Regular;
    .title
      margin 20px 0 0 24px
      font-size:18px;
      color:#ffffff;
      text-align:left;
      line-height:24px;
      letter-spacing 2px
    .data
      display flex
      margin-left 24px
      width 480px
      height 314px
      justify-content: space-between;
      flex-wrap: wrap;
      .data-list
        position relative
        width 160px
        height 157px
        text-align center
        color #fff
        .bg-img
          margin 10px auto
          width 90px
          height 46px
          border 6px solid #221d3c
          border-radius 50px 50px 0 0
          border-bottom none
        .data-chars
          position: absolute
          top 8px
          left 27px
        .data-chars1
          position: absolute
          top 8px
          left 27px
        .data-chars2
          position: absolute
          top 8px
          left 27px
        .data-chars3
          position: absolute
          top 8px
          left 27px
        .data-chars4
          position: absolute
          top 8px
          left 27px
        .data-chars5
          position: absolute
          top 8px
          left 27px
        .scale-img
          position absolute
          top 12px
          left 4px
          width 90px
          height 46px
        .long
          top 9px
          left 19px
        .icon-img
          position absolute
          top 32px
          left 66px
          img
            width 26px
            height 60px
        .data-p1
          margin-top 29px
          font-size 20px
        .temperature
          color #00ddf2
        .humidity
          color #c3ff58
        .pm10
          color #c56cd7
        .pm2
          color #45f1bb
        .formaldehyde
          color #f8a640
        .tovc
          color #92e88c
        .data-title
          font-size 14px
          margin-top 6px
</style>
