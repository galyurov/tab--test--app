<template>
   <div class="tabs">
      <div class="tabs--head">
         <div 
            v-for="(tab) in tabs" 
            :key="tab.name" 
            class="tab"
            :class="{'tab-active' : tab.isActive}"
            @click="activateTab(tab)"
         >
            <div class="tab--text">
               {{tab.name}}  
            </div>
         </div>
      </div>
      <div ref="tabItemWrap" class="tabs--content">
         <slot/>
      </div>
      <!-- Не до конца понял задачу, поэтому сделал это поле для пользовательского ввода названия таба и его контента -->
      <div class="tabs--add">
         <input v-model="addTabName" class="add--input" type="text" placeholder="Input tab name">
         <textarea v-model="addTabContent" class="add--input" rows="20" placeholder="Input Content"></textarea>
         <button @click="addTab" class="add--button">Add</button>
      </div>
   </div>
</template>
<script>
import TabItem from './TabItem.vue';
import Vue from 'vue'
export default {
	name:'Tabs', 
   data(){
      return {
         tabs: null,
         addTabName: null,
         addTabContent: null,
      }
	},
	methods:{
      activateTab(item){
         this.tabs.forEach(element => {
            element.isActive = false
         });
         item.isActive = true
      },
      addTab(){
         if(this.addTabName && this.addTabContent){
            let newTabClass = Vue.extend(TabItem)
            let newTab = new newTabClass({
               propsData: {name: this.addTabName}
            })
            const node = newTab.$createElement('div', [this.addTabContent])
            newTab.$slots.default = [node];
            newTab.$mount()
            this.$refs.tabItemWrap.appendChild(newTab.$el)
            this.$children.push(newTab)
            this.addTabName = null
            this.addTabContent = null
         }
        
      }
   },
   created(){
      this.tabs = this.$children
   }
}
</script>
<style lang='scss' scoped>
.tabs{
   width:75vw;
   &--head{
      display: flex;
      align-items: center;
      padding: 0 5px;
      &::-webkit-scrollbar{
         display: none;
      }
   }
   .tab{
      min-width: 20px;
      background-color: #807b7b;
      border-radius: 4px 4px 0 0;
      padding: 4px 10px;
      cursor: default;

      &.tab-active{
         background-color: #ffffff;
         position: relative;
      }
   }
   .tab--text{
      overflow: hidden;
      white-space: nowrap;
      text-overflow: ellipsis;
   
   }
   .tab--close{
      width: 15px;
      height: 15px;
      margin-left: 5px;
      text-align: center;
      justify-self: end;
   }
   .tabs--content{
      background-color: #ffffff;
      padding: 10px;
      border-radius: 4px;
   }
   .tabs--add{
      display: flex;
      flex-direction: column;
      align-items: center;
      width: 100%;
      margin-top: 20px;
      background-color: #ffffff;
      border-radius: 4px;
      padding-bottom: 10px;
      .add--input{
         margin: 5px;
         width: 90%;
      }
      .add--button{
         border: none;
         border-radius: 4px;
         background-color: #1c7c1c;
         padding: 5px;
         width: 20%;
      }
   }
}
</style>