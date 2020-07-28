<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
  }
  #app{
    position: relative;
    width: 1920px;
    height: 1072.4px;
    background: #09001A;
    color: #fff;
    font-family:PingFangSC-Regular;
  }
  ul li{
    list-style: none;
  }
</style>
