<template>
    <div class="smartfactory">
      <p class="title">智慧工厂</p>
      <div class="factory">
        <div class="factory-left">
          <p class="left-title">厂内仓库监测环境监控</p>
          <div class="left-content">
            <div class="con-left">
              <div class="room">
                <div class="block bl-1"></div>
                <div class="block bl-2"></div>
                <div class="block bl-3"><span>空调</span></div>
                <div class="img1">
                  <img src="../../images/贴图/E66E4D50-BFEB-4DFB-98E4-09DB29F49DC3@1x.png" alt="">
                </div>
                <div class="img2">
                  <img src="../../images/贴图/8CF8B87A-41E9-4545-81AB-D0B505AEA569@1x.png" alt="">
                </div>
                <p class="room-name">配电室</p>
                <div class="mask"></div>
              </div>
              <div class="door">
                <div class="door-img1 hand">
                  <el-button type="text" @click="dialogVideoVisible = true" title="监控视频展示">
                    <img src="../../images/贴图/72AA17F8-B2F8-452C-8F06-FBABDC08B58E@1x.png" alt="">
                  </el-button>
                  <el-dialog title="监控视频展示" width="580px" :visible.sync="dialogVideoVisible">
                    <video-player
                      ref="videoPlayer"
                      :options="playerOptions"
                      :playsinline="true"
                      class="video-player vjs-custom-skin"
                    >
                    </video-player>
                  </el-dialog>
                </div>
                <div class="door-img2" ><img src="../../images/贴图/667B4BB7-33D0-4988-9E84-6A3402784EA5@1x.png" alt=""></div>
                <div class="door-img3" ><img src="../../images/贴图/6F307965-96D4-4220-8F0D-5D5B65EA3968@1x.png" alt=""></div>
                <div class="door-mask"></div>
              </div>
            </div>
            <div class="con-right">
              <div class="right-block block1"><span>空调</span></div>
              <div class="right-block block2"><span>空调</span></div>
              <div class="right-block block3"><span>空调</span></div>
              <div class="right-block block4"><span>空调</span></div>
              <div class="locker">
                <ul class="locker-list">
                  <li class="locker-unique">储物柜1</li>
                  <li class="locker-img">
                    <el-button type="text" @click="dialogTableVisible = true" title="温度传感器1">
                      <img class="locker-img1 hand" src="../../images/贴图/6D483540-042A-43F7-A35B-E42EBBAE7097@1x.png" alt="">
                    </el-button>
                    <el-dialog title="温度传感器1 趋势图" :visible.sync="dialogTableVisible">
                      <ve-line :data="chartData" :settings="chartSettings"></ve-line>
                    </el-dialog>

                    <!--<img class="locker-img2 hand" src="../../images/贴图/431DA061-90CF-4FA9-BB9C-8DF6DA74EDCD@1x.png" alt="">-->
                    <el-button type="text" @click="dialogHumidityVisible = true" title="湿度传感器1">
                      <img class="locker-img2 hand" src="../../images/贴图/431DA061-90CF-4FA9-BB9C-8DF6DA74EDCD@1x.png" alt="">
                    </el-button>
                    <el-dialog title="湿度传感器1 趋势图" :visible.sync="dialogHumidityVisible">
                      <ve-line :data="chartData2" :settings="chartSettings2"></ve-line>
                    </el-dialog>
                    <img class="locker-img3" src="../../images/贴图/8CF8B87A-41E9-4545-81AB-D0B505AEA569@1x.png" alt="">
                  </li>
                  <li class="locker-unique">储物柜2</li>
                  <li class="locker-img">
                    <img class="locker-img4" src="../../images/贴图/8CF8B87A-41E9-4545-81AB-D0B505AEA569@1x.png" alt="">
                  </li>
                  <li class="locker-unique">储物柜3</li>
                  <li class="locker-img">

                    <el-button type="text" @click="dialogTable2Visible = true" title="温度传感器2">
                      <img class="locker-img5" src="../../images/贴图/6D483540-042A-43F7-A35B-E42EBBAE7097@1x.png" alt="">
                    </el-button>
                    <el-dialog title="温度传感器2 趋势图" :visible.sync="dialogTable2Visible">
                      <ve-line :data="chartData3" :settings="chartSettings3"></ve-line>
                    </el-dialog>

                    <el-button type="text" @click="dialogHumidity2Visible = true" title="湿度传感器2">
                      <img class="locker-img6" src="../../images/贴图/431DA061-90CF-4FA9-BB9C-8DF6DA74EDCD@1x.png" alt="">
                    </el-button>
                    <el-dialog title="湿度传感器2 趋势图" :visible.sync="dialogHumidity2Visible">
                      <ve-line :data="chartData4" :settings="chartSettings4"></ve-line>
                    </el-dialog>

                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
        <div class="factory-right">
          <p class="right-title">边缘计算能力</p>
          <ul class="right-list">
            <li class="li-list">
              <div class="li-left">
                <img src="../../images/贴图/AF0BC063-4B60-4F1C-99C8-D4D7D38AD5FF@1x.png" alt="">
                <p>主机状态</p>
              </div>
              <div class="li-right">正常</div>
            </li>
            <li class="li-list">
              <div class="li-left">
              <img src="../../images/贴图/138CB419-2299-49E8-B89A-0D747D0C7B3F@1x.png" alt="">
              <p>业务逻辑</p>
              </div>
              <div class="li-right">平均值计算</div>
            </li>
            <li class="li-list">
              <div class="li-left">
                <img class="img3" src="../../images/贴图/6AED3812-3FB9-47DB-82DC-17756E41B26A@1x.png" alt="">
                <p>平均温度</p>
              </div>
              <div class="li-right">23.3 ℃</div>
            </li>
            <li class="li-list">
              <div class="li-left">
                <img class="img4" src="../../images/贴图/2F200C76-6A0C-4C87-A6D9-E35315B2DF5E@1x.png" alt="">
                <p class="p-last">平均温度</p>
              </div>
              <div class="li-right">62%</div>
            </li>
          </ul>
        </div>
      </div>
    </div>
</template>

<script>
    export default {
        name: "Smartfactory",
        data() {
            this.chartSettings = {
              metrics: ['温度']
            }
            this.chartSettings2 = {
              metrics: ['湿度']
            }
            this.chartSettings3 = {
              metrics: ['温度']
            }
            this.chartSettings4 = {
              metrics: ['湿度']
            }
            return {
              videoUrl: 'http://47.94.45.9:2943/live/0018ae7f0da2.m3u8',
              chartData: {
                columns: ['时间', '温度'],
                rows: [
                  { '时间': '14:00', '温度': 10},
                  { '时间': '14:10', '温度': 25},
                  { '时间': '14:20', '温度': 28},
                  { '时间': '14:30', '温度': 32.8},
                  { '时间': '14:40', '温度': 33.2},
                  { '时间': '14:50', '温度': 24},
                  { '时间': '15:00', '温度': 15}
                ]
              },
              chartData2: {
                columns: ['时间', '湿度'],
                rows: [
                  { '时间': '14:00', '湿度': 5},
                  { '时间': '14:10', '湿度': 15},
                  { '时间': '14:20', '湿度': 25},
                  { '时间': '14:30', '湿度': 32},
                  { '时间': '14:40', '湿度': 35},
                  { '时间': '14:50', '湿度': 24},
                  { '时间': '15:00', '湿度': 15}
                ]
              },
              chartData3: {
                columns: ['时间', '温度'],
                rows: [
                  { '时间': '14:00', '温度': 5},
                  { '时间': '14:10', '温度': 10},
                  { '时间': '14:20', '温度': 22},
                  { '时间': '14:30', '温度': 32.8},
                  { '时间': '14:40', '温度': 35},
                  { '时间': '14:50', '温度': 24},
                  { '时间': '15:00', '温度': 15}
                ]
              },
              chartData4: {
                columns: ['时间', '湿度'],
                rows: [
                  { '时间': '14:00', '湿度': 7},
                  { '时间': '14:10', '湿度': 24},
                  { '时间': '14:20', '湿度': 29},
                  { '时间': '14:30', '湿度': 32},
                  { '时间': '14:40', '湿度': 35},
                  { '时间': '14:50', '湿度': 24},
                  { '时间': '15:00', '湿度': 10}
                ]
              },
              dialogTableVisible: false,
              dialogVideoVisible: false,
              dialogHumidityVisible: false,
              dialogTable2Visible: false,
              dialogHumidity2Visible: false,
              playerOptions: {
                width:540,  //播放器宽度
                height:300,  //播放器高度
                muted: true,
                flash: {
                  hls: { withCredentials: false },
                  swf: '/swf/video-js.swf'
                  //使用flash时要引入该文件，可以在npm安装文件夹的相应模块文件夹中找到。
                },
                html5: { hls: { withCredentials: false } },
                techOrder: ['flash','html5'],  //技术流，优先使用flash播放，不支持则使
                //用html5播放。
                sources:[  //数据源配置
                  {
                    type: "application/x-mpegURL",  //视频流类型，支持rtmp,md3u等
                    src: this.videoUrl // 你的m3u8地址（必填）
                  }
                ],
                //notSupportedMessage: '此视频暂无法播放，请稍后再试'// 允许覆盖Video.js无法播放媒体源时显示的默认信息。
              }

            }
        },
        methods: {
          open() {
            this.$alert('<strong>这是 <i>HTML</i> 片段</strong>', 'HTML 片段',  {
              dangerouslyUseHTMLString: true
            })
          }
        }
    }
</script>

<style scoped lang="stylus">
  .hand
    cursor pointer
  .smartfactory
    position absolute
    left: 700px;
    top: 86px;
    color: #fff;
    .title
      font-family:PingFangSC-Regular;
      font-size:20px;
      color:#ffffff;
      letter-spacing:-0.21px;
      text-align:left;
    .factory
      width: 1212px;
      height:542px;
      margin-top: 10px;
      font-family:PingFangSC-Regular;
      .factory-left
        float: left;
        background-image:linear-gradient(-51deg, rgba(11,15,86,0.55) 0%, rgba(9,9,57,0.31) 99%);
        border-radius:8px;
        width:876px;
        height:542px;
        .left-title
          padding 20px
          box-sizing border-box
          font-size:16px;
          color:#ebeef5;
          text-align:left;
          line-height:22px;
        .left-content
          position relative
          margin 0 auto
          border:4px solid #383657;
          width:832px;
          height:456px;
          .con-left
            width: 264px;
            height: 100%;
            .room
              position relative
              width:256px;
              height:256px;
              border: 4px solid #383657;
              border-top: none;
              border-left: none;
              .block
                opacity:0.6;
                background:#333652;
                border-radius:2px;
                width:50px;
                height:50px;
              .bl-1
                position absolute
                left: 50px;
                top: 60px;
              .bl-2
                position absolute
                right: 50px;
                top: 60px;
              .bl-3
                position absolute
                right: 0;
                bottom: 0;
                box-shadow:2px 2px 4px 0 #000000;
                text-align center
                line-height: 50px;
                opacity:0.5;
                font-size 14px
            .img1
              position absolute
              left 60px
              top 120px
            .img2
              position absolute
              right 60px
              top 108px
            .room-name
              position absolute
              left 108px
              top 169px
              opacity:0.5;
              font-size:14px;
              color:#ffffff;
              text-align:left;
            .mask
              position absolute
              left 50px
              bottom -4px
              width: 106px;
              height 4px
              background: #0a052d;
            .door
              height 200px
              position relative
              .door-img1
                position absolute
                height 28px
                left 68px
                top 150px
                bottom 12px
              .door-img2
                position absolute
                left 108px
                bottom 3px
                border:1px solid #383657;
                border-top none
                border-right none
                width:56px;
                height:56px;
              .door-img3
                position absolute
                left 165px
                bottom 3px
                border:1px solid #383657;
                border-left none
                border-top none
                width:58px;
                height:56px;
              .door-mask
                position absolute
                left 109px
                bottom 0
                width: 115px;
                height 4px
                background: #0a052d;
          .con-right
            position absolute
            width 576px
            height 100%
            left 260px
            top 0
            .right-block
              position absolute
              opacity:0.6;
              background:#333652;
              border-radius:2px;
              width:50px;
              height:50px;
              text-align center
              line-height: 50px;
              font-size 14px
             .block2
               right 0
               top 0
             .block3
               right 0
               bottom 0
             .block4
               left 20px
               bottom 0
          .locker
            position absolute
            left 96px
            top 60px
            width 420px
            height 360px
            .locker-list
              height 100%
              li
                position relative
                height 60px
                border-radius:2px;
                font-size:14px;
                letter-spacing 1px
              .locker-unique
                opacity:0.5;
                text-align center
                line-height 60px
                background:#2b2950;
                box-shadow:4px 4px 10px 0 #000000;
              .locker-img
                .locker-img1
                  position absolute
                  left 10px
                  bottom -12px
                .locker-img2
                  position absolute
                  left 100px
                  bottom -20px
                .locker-img3
                  position absolute
                  right -40px
                  top -70px
                .locker-img4
                  position absolute
                  left 10px
                  bottom -12px
                .locker-img5
                  position absolute
                  right 100px
                  bottom -13px
                .locker-img6
                  position absolute
                  right 10px
                  bottom -24px
      .factory-right
        float right
        padding 20px 0 0 40px
        box-sizing border-box
        width 336px
        height 542px
        .right-title
          font-size:16px;
          color:#ebeef5;
          text-align:left;
          line-height:22px;
        .right-list
          margin-top 10px
          height 500px
          .li-list
            height 96px
            margin-top 20px
            .li-left
              float left
              width 96px
              height 96px
              img
                width 57px
                height 67px
              .img3
                width 46px
                height 77px
                margin-left 3px
              .img4
                width 46px
                height 96px
                margin-left 5px
              p
                width 100%
                font-family:PingFangSC-Regular;
                font-size:14px;
                color:#4a6ce2;
                text-align:left;
              .p-last
                margin-top -12px
            .li-right
              float right
              width 180px
              height 96px
              line-height 96px
              font-family:Arial-Black;
              font-size:30px;
              color:#ebeef5;
              text-align:left;
</style>
