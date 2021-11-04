<template>
  <div class="homeWrapper" v-bind:class="{'homeWrapperMobile':mobile}">
    <image-shoes></image-shoes>
    <information></information>
  </div>
</template>

<script>
import image from '../components/image.vue'
import information from '../components/information.vue'
export default {
    name:'home',
    components:{
      'imageShoes':image,
      'information':information,
    },
    data(){
      return{
        windowWidth:null,
      }
    },
    props:{
      mobile:Boolean,
    }
    // created(){
    //   this.width();
    // },
    // methods:{
    //   width:function(){
    //     this.windowWidth=window.innerWidth;
    //   }
    // }
}
</script>

<style lang="scss" scoped>
  .homeWrapper{
    display: grid;
    grid-template-columns: repeat(2,1fr);
    grid-column-gap: 1rem;
  }
  .homeWrapperMobile{
    grid-template-columns:initial;
    grid-column-gap:initial;
    grid-template-rows: repeat(2,1fr);
  }
</style>