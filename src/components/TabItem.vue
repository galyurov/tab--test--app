<template>
   <div 
   :name='name'
   class="tab--item" 
   :class="{'tab--item--active': isActive }"
   >
      <slot/>
   </div>
</template>
<script>
export default {
    name:'TabItem',
    data(){
       return {
          isActive: false,
       }
    },
    props:{
        name:{
           required: true,
           type: String
        }
   }
}
</script>
<style lang='scss' scoped>
.tab--item{
   display: none;
   &.tab--item--active{
      display: block;
   }
}
</style>