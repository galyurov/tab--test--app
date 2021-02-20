<template>
    <div class="tabs">
        <div class="tabs__head">
            <div 
               v-for="(tab) in tabs" 
               :key="tab.name" 
               class="tab"
               :class="{'tab-active' : tab.isActive}"
               @click="activateTab(tab)"
            >
               <div class="tab__text">
                  {{tab.name}}  
               </div>
            </div>
            <div class="tab__add">+</div>
        </div>
        <div class="tabs__content">
            <slot/>
        </div>
    </div>
</template>
<script>
export default {
	name:'Tabs', 
		data(){
         return {
            tabs:null
         }
	},
	methods:{
      activateTab(item){
         this.tabs.forEach(element => {
            element.isActive = false
         });
         item.isActive = true
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
    &__head{
      display: flex;
      align-items: center;
      padding: 0 5px;
    }
    .tab{
       display: flex;
       align-items: center;
       max-width: 200px;
       background-color: #807b7b;
       border-radius: 4px 4px 0 0;
       padding: 4px 10px;
       cursor: default;

       &.tab-active{
         background-color: #ffffff;
         position: relative;
       }
    }
    .tab__close{
       width: 15px;
       height: 15px;
       margin-left: 5px;
       text-align: center;
       justify-self: end;
    }
    .tabs__content{
       background-color: #ffffff;
       padding: 10px;
       border-radius: 4px;
    }
}
</style>