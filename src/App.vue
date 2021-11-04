<template>
  <div class="appWrapper">
    <header-top :mobile="mobile"></header-top>
    <router-view v-bind:mobile="mobile"></router-view>
  </div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    'header-top':Header
  },
  data(){
    return{
      mobile:null,
      windowWidth:null
    }
  },
  created(){
    window.addEventListener('resize',this.checkScreen);
    this.checkScreen()
  },
  methods:{
    checkScreen:function(){
      this.windowWidth=window.innerWidth;
      if(this.windowWidth<=750){
        this.mobile=true
        return;
      }
      else{
        this.mobile=false
        return;
      }
    }
  }
}
</script>

<style lang="scss">
    $Orange: hsl(26, 100%, 55%);
    $Pale-orange: hsl(25, 100%, 94%);
    $Very-vark-blue: hsl(220, 13%, 13%);
    $Dark-grayish-blue: hsl(219, 9%, 45%);
    $Grayish-blue: hsl(220, 14%, 75%);
    $Light-grayish-blue: hsl(223, 64%, 98%);
    $Font-size: 16px;

    *{
      padding: 0;
      margin: 0;
      box-sizing: border-box;
    }
    .appWrapper{
      max-width: 1440px;
    }
</style>
