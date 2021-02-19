<template>
  <div class="app" id="app">
    <tab-view/>
  </div>
</template>

<script>
import TabView from './components/TabView.vue'
export default {
  name: 'App',
  components:{
    TabView
  }
}
</script>
<style>
body{
  background-color: #919191;
}
  .app{
      display: flex;
      justify-content: center;
      margin-top: 30px;
  }
</style>