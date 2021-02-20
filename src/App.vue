<template>
  <div class="app" id="app">
    <tabs>
       <!-- tab component get name as attribute -->
      <tab-item 
        name="Custom tab 1"
      >
      <!-- tab component get content in tag tab-item -->
        <h2>Some head in custom tab</h2>
        <input type="text">
        <button>Save</button>
      </tab-item>

      <tab-item 
        name="Custom tab 2"
      >
        <div>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ullam nesciunt est consequuntur aperiam magnam voluptate optio? In ipsa molestias debitis? Ex vero in exercitationem repudiandae error enim nulla possimus expedita!</div>
      </tab-item>

      <tab-item 
        name="Custom tab 3"
      >
        <h3>Some head 3</h3>
        <textarea name="" id="" cols="30" rows="10"></textarea>
        <button>Save</button>
      </tab-item>

      <tab-item 
        name="Custom tab 4"
      >
        <h3>Some head </h3>
        <button>Save</button>
      </tab-item>
    </tabs>
  </div>
</template>

<script>
import Tabs from './components/Tabs.vue'
import TabItem from './components/TabItem.vue'
export default {
  name: 'App',
  components:{
    Tabs,
    TabItem
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