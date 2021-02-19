<template>
    <div class="tabs">
        <div class="tabs__head">
            <div 
               v-for="(item,index) in tabs" 
               :key="item" 
               class="tab"
               :class="{'tab-active' : tab===item}"
               @click="tab = item"
            >
               <div class="tab__text">
                  {{item}}  
               </div>
               <div @click.stop="closeTab(index)" class="tab__close">
                 <img src="../assets/icons/cancel.svg" alt="close">
               </div>
            </div>
            <div @click="addTab" class="tabs__add">
               +
            </div>
        </div>
        <div class="tabs__content">
            Some text from tab, or some content
        </div>
    </div>
</template>
<script>
export default {
    name:'TabView', 
    data(){
        return {
            tab:'tab1',
            tabs:['tab1', 'tab2']
        }
    },
    methods:{
       closeTab(i){
          this.tabs.splice(i,1)
       },
       addTab(){
          this.tabs.push(`tab${this.tabs.length+1}`)
       }
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
       padding: 4px 5px 4px 10px;
       cursor: default;
       &:last-child{
          margin-right: 0;
       }
       &.tab-active{
         background-color: #ffffff;
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
    .tabs__add{
       width: 20px;
       height: 20px;
       display: flex;
       justify-content: center;
       align-items: center;
       font-size: 24px;
       border-radius: 50%;
       margin-left: 5px; 
       cursor: pointer; 
       &:hover{
         background-color: #ffffff;
       }
    }
}
</style>