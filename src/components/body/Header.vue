<template>
    <div class="header">
      <div class="title">
        <img class="img1" src="../../images/贴图/header-4.png" alt="">
        <img class="img2" src="../../images/贴图/header-5.png" alt="">
      </div>
    </div>
</template>

<script>
    export default {
        name: "Header",
        data() {
            return {}
        }
    }
</script>

<style scoped lang="stylus">
  .header
    width: 1920px
    height: 70px
    background: #09001A
    .title
      position relative
      height 100%
      .img1
        width 1166px
      .img2
        position absolute
        width 749px
        left 1166px

        

</style>
