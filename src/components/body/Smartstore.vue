<template>
    <div class="smartstore">
      <p class="title">智慧门店</p>
      <div class="data">
        <ul class="list">
          <li v-for="storeData in storeDatas">
            <p class="mount">{{storeData.amount}}</p>
            <p class="descript">{{storeData.title}}</p>
          </li>
        </ul>
      </div>
      <div class="chart"></div>
      <div class="volume"></div>
    </div>
</template>

<script>
    export default {
        name: "Smartstore",
        data() {
            return {
              storeDatas: [
                {title: '在线人数', amount: 1345},
                {title: '进店人数', amount: 234},
                {title: '客流总数', amount: 3456},
                {title: '平均停留时长(min)', amount: 21}
              ]
            }
        },
        mounted(){
          this.drawLine()
          this.drawLine2()
        },
        methods: {
          drawLine(){
            let oChart = document.getElementsByClassName('chart')[0]
            let myChart = this.$echarts.init(oChart)

            myChart.setOption({
              title: {
                text: '实时客流量（进店）',
                textStyle: {
                  color: '#ebeef5',
                  fontWeight: 'normal'
                }
              },
              tooltip: {},
              xAxis: {
                data: ['14:00', '14:10', '14:20', '14:30', '14:40', '14:50', '15:00'],
                splitLine: {show: false},
                axisLine: {
                  show: true,
                  lineStyle: {
                    type: 'solid',
                    color: '#2f2b48',//轴线的颜色
                    width:'1.5'//坐标线的宽度
                  }
                },
                axisTick: {//刻度
                  show: false//不显示刻度线
                },
                axisLabel: {
                  textStyle: {
                    color: '#878787',//坐标值的具体的颜色
                  }
                },
              },
              // backgroundColor: '#fff',//图得背景色
              yAxis: {
                // data: ['32', '32.2', '32.4', '32.6'],
                max: 32.6,
                min: 32,
                axisLine: {//线
                  show: false
                },
                axisTick: {//刻度
                  show: false
                },
                axisLabel: {
                  textStyle: {
                    color: '#878787',//坐标值得具体的颜色
                  }
                },
                minInterval: 0.2,//标值的最小间隔
                splitLine: {
                  lineStyle: {
                    type: 'dashed',
                    color: ['#2f2b48'],//分割线的颜色
                    width: '1.5'
                  }
                }
              },
              series: [{
                name: '进店人数',//每组数据的名字，与图例对应
                data: [32.04, 32.20, 32.34, 32.58, 32.46, 32.32, 32.26],//数据
                type: 'line',//折线图
                itemStyle: {
                  normal: {
                    color: '#00e3de',//设置折线颜色
                    label: {
                      show: true,//图上显示值
                      position: 'top',//值在柱子上方显示
                      textStyle: {
                        color: '#00e3de'//值得颜色
                      }
                    }
                  }
                },
                areaStyle: {
                  color: {
                    type: 'linear',
                    x: 0,
                    y: 0,
                    x2: 0,
                    y2: 1,
                    colorStops: [{
                      offset: 0, color: '#00e3de' // 0% 处的颜色
                    }, {
                      offset: 1, color: '#0a0734' // 100% 处的颜色
                    }],
                    global: false // 缺省为 false
                  }
                }
              }]
            })
          },
          drawLine2(){
            let oChart = document.getElementsByClassName('volume')[0]
            let myChart = this.$echarts.init(oChart)

            myChart.setOption({
              title: {
                text: '实时客流量（穿行）',
                textStyle: {
                  color: '#ebeef5',
                  fontWeight: 'normal'
                }
              },
              tooltip: {},
              xAxis: {
                data: ['14:00', '14:10', '14:20', '14:30', '14:40', '14:50', '15:00'],
                splitLine: {show: false},
                axisLine: {
                  lineStyle: {
                    type: 'solid',
                    color: '#2f2b48',//轴线的颜色
                    width:'1.5'//坐标线的宽度
                  }
                },
                axisTick: {//刻度
                  show: false//不显示刻度线
                },
                axisLabel: {
                  textStyle: {
                    color: '#878787',//坐标值的具体的颜色
                  }
                },
              },
              // backgroundColor: '#fff',//图得背景色
              yAxis: {
                max: 32.6,
                min: 32,
                axisLine: {//线
                  show: false
                },
                axisTick: {//刻度
                  show: false
                },
                axisLabel: {
                  textStyle: {
                    color: '#878787',//坐标值得具体的颜色
                  }
                },
                minInterval: 0.2,//标值的最小间隔
                splitLine: {
                  lineStyle: {
                    type: 'dashed',
                    color: ['#2f2b48'],//分割线的颜色
                    width: '1.5',
                  }
                }
              },
              series: [{
                name: '穿行人数',//每组数据的名字，与图例对应
                data: [32.32, 32.20, 32.25, 32.38, 32.58, 32.32, 32.23],//数据
                type: 'line',//折线图
                itemStyle: {
                  normal: {
                    color: '#00e3de',//设置柱子颜色
                    label: {
                      show: true,//柱子上显示值
                      position: 'top',//值在柱子上方显示
                      textStyle: {
                        color: '#00e3de'//值得颜色
                      }
                    }
                  }
                },
                areaStyle: {
                  color: {
                    type: 'linear',
                    x: 0,
                    y: 0,
                    x2: 0,
                    y2: 1,
                    colorStops: [{
                      offset: 0, color: '#00e3de' // 0% 处的颜色
                    }, {
                      offset: 1, color: '#1d1e5e' // 100% 处的颜色
                    }],
                    global: false // 缺省为 false
                  }
                }
              }]
            })
          }
        }
    }
</script>

<style scoped lang="stylus">
  .smartstore
    color: #fff
    width: 640px
    margin: 16px 40px 24px 24px
    .title
      font-family:PingFangSC-Regular
      font-size:20px
      letter-spacing:-0.21px
      text-align:left
    .data
      margin-top: 10px;
      opacity:0.9;
      background-image:linear-gradient(-180deg, #0a083b 0%, rgba(9,4,38,0.00) 52%, #0a083b 100%);
      border-radius:8px;
      width:640px;
      height:120px;
      .list
        padding-top: 42px;
        li
          float: left;
          width: 160px;
          .mount
            font-size: 30px;
            color: #65ccf4;
            font-weight: 800;
            text-align:center;
          .descript
            margin-top: 8px;
            font-family:PingFangSC-Regular;
            font-size:14px;
            color:#ffffff;
            letter-spacing:-0.39px;
            text-align:center;
    .chart
      position relative
      margin-top: 24px;
      background-image:linear-gradient(-51deg, rgba(11,15,86,0.55) 0%, rgba(9,9,57,0.31) 99%);
      border-radius:8px;
      width:635px;
      height:378px;
      box-sizing border-box
      padding 20px
      .chart-title
        padding: 20px;
        padding-bottom 0
        box-sizing border-box
        font-family:PingFangSC-Regular;
        font-size:18px;
        color:#ebeef5;
        text-align:left;
        line-height:28px;
      .chart-list
        margin: 0 20px 0 53px;
        li
          position: relative;
          height: 70px;
          opacity:0.5;
          border-bottom:1px dotted #e9e9e9;
          span
            position absolute
            left: -30px;
            bottom: -10px;
            font-size:12px;
            color:#ebeef5;
            text-align:right;
            line-height:20px;
        .last
          border-bottom:1px solid #e9e9e9;
      .chart-time
        span
          opacity:0.5;
          margin-left: 56px;
          font-size:12px;
          color:#ebeef5;
          text-align:left;
          line-height:34px;
      .bg-img
        position absolute
        left: 72px;
        top: 125px;
        width:518px;
        height:188px;
        img
          width: 100%;
          height: 100%;
        /*.img2*/
          /*position: absolute*/
          /*top: 125px;*/
    .volume
      position relative
      margin-top: 25px;
      margin-bottom: 22px;
      background-image:linear-gradient(-180deg, #0a102d 0%, #212169 100%);
      border-radius:8px;
      width:639px;
      height:381px;
      box-sizing border-box
      padding 20px
      .volume-title
        padding: 20px;
        padding-bottom 0
        box-sizing border-box
        font-family:PingFangSC-Regular;
        font-size:18px;
        color:#ebeef5;
        text-align:left;
        line-height:28px;
      .volume-list
        margin: 0 20px 0 53px;
        li
          position: relative;
          height: 70px;
          opacity:0.5;
          border-bottom:1px dotted #e9e9e9;
          span
            position absolute
            left: -30px;
            bottom: -10px;
            font-size:12px;
            color:#ebeef5;
            text-align:right;
            line-height:20px;
        .last
          border-bottom:1px solid #e9e9e9;
      .volume-time
        span
          opacity:0.5;
          margin-left: 56px;
          font-size:12px;
          color:#ebeef5;
          text-align:left;
          line-height:34px;
      .bg-img
        position absolute
        left: 72px;
        top: 125px;
        width:518px;
        height:188px;
        img
          width: 100%;
          height: 100%;
</style>
