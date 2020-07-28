<template>
    <div class="index">
      <Header></Header>
      <Smartstore></Smartstore>
      <Smartfactory></Smartfactory>
      <Monitoring></Monitoring>
      <Warningmes></Warningmes>
    </div>
</template>

<script>
  import Header from './body/Header'
  import Smartstore from './body/Smartstore'
  import Smartfactory from './body/Smartfactory'
  import Monitoring from './body/Monitoring'
  import Warningmes from './body/Warningmes'
    export default {
        name: "Index",
        data() {
            return {}
        },
      components: {
        Header,
        Smartstore,
        Smartfactory,
        Monitoring,
        Warningmes
      }
    }
</script>

<style scoped>

</style>
