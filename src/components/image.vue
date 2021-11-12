<template>
  <div class="imageWrapper ">
      <div v-if="!mobile" class="currentImage">
            <img v-on:click="showImage" :src="require('../../images/'+bigImage)" alt="product">
      </div>
        <div v-if="mobile" v-on:click="previousToggleMobile" class="toggleLeft">
            <svg width="12" height="18" xmlns="http://www.w3.org/2000/svg"><path d="M11 1 3 9l8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd"/></svg>
        </div>
        <img v-if="mobile" :src="require('../../images/'+bigImage)" alt="product">
        <div v-if="mobile" v-on:click="nextToggleMobile" class="toggleRight">
            <svg width="13" height="18" xmlns="http://www.w3.org/2000/svg"><path d="m2 1 8 8-8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd"/></svg>
        </div>
      <div v-if="!mobile" class="bottomImage">
          <div ref="thumbnail1" v-on:click=" toggleP1();Overlay1()" class="overlay defaultO">
            <img class="thumbnail"  src="../../images/image-product-1-thumbnail.jpg" alt="product-th">
          </div>
          <div ref="thumbnail2" v-on:click=" toggleP2();Overlay2()" class="overlay">
            <img class="thumbnail" src="../../images/image-product-2-thumbnail.jpg" alt="product-th">
          </div>
          <div ref="thumbnail3" v-on:click=" toggleP3();Overlay3()" class="overlay">
            <img class="thumbnail" src="../../images/image-product-3-thumbnail.jpg" alt="product-th">
          </div>
          <div ref="thumbnail4" v-on:click=" toggleP4();Overlay4()" class="overlay">
            <img  class="thumbnail" src="../../images/image-product-4-thumbnail.jpg" alt="product-th">
          </div>
      </div>
      <div v-if="image" class="modal">
          <div v-on:click="showImage" class="modalOverlay"></div>
          <div  class="modalContent">
                <div v-on:click="showImage" class="close">
                    <svg width="14" height="15" xmlns="http://www.w3.org/2000/svg"><path d="m11.596.782 2.122 2.122L9.12 7.499l4.597 4.597-2.122 2.122L7 9.62l-4.595 4.597-2.122-2.122L4.878 7.5.282 2.904 2.404.782l4.595 4.596L11.596.782Z" fill="#69707D" fill-rule="evenodd"/></svg>
                </div>
                <div class="currentImage modalCurrentImage">
                    <div v-on:click="previousToggle" class="toggleLeft">
                        <svg width="12" height="18" xmlns="http://www.w3.org/2000/svg"><path d="M11 1 3 9l8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd"/></svg>
                    </div>
                    <img :src="require('../../images/'+bigImageModal)" alt="product">
                    <div v-on:click="nextToggle" class="toggleRight">
                        <svg width="13" height="18" xmlns="http://www.w3.org/2000/svg"><path d="m2 1 8 8-8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd"/></svg>
                    </div>
                </div>
                <div class="bottomImage modalBottomImage">
                    <div ref="thumbnailM1" v-on:click=" toggleModalP1();OverlayM1() " class="overlay defaultO">
                        <img class="thumbnail"  src="../../images/image-product-1-thumbnail.jpg" alt="product-th">
                    </div>
                    <div ref="thumbnailM2" v-on:click=" toggleModalP2();OverlayM2() " class="overlay">
                        <img class="thumbnail" src="../../images/image-product-2-thumbnail.jpg" alt="product-th">
                    </div>
                    <div ref="thumbnailM3" v-on:click=" toggleModalP3(); OverlayM3() " class="overlay">
                        <img class="thumbnail" src="../../images/image-product-3-thumbnail.jpg" alt="product-th">
                    </div>
                    <div ref="thumbnailM4" v-on:click=" toggleModalP4(); OverlayM4() " class="overlay">
                        <img  class="thumbnail" src="../../images/image-product-4-thumbnail.jpg" alt="product-th">
                    </div>
                </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name:'image',
    data(){
        return{
            image:false,
            product1:"image-product-1.jpg",
            product2:"image-product-2.jpg",
            product3:"image-product-3.jpg",
            product4:"image-product-4.jpg",
            bigImage:"image-product-1.jpg",
            bigImageModal:"image-product-1.jpg",
        }
    },
    props:{
        mobile:Boolean
    },
    methods:{
        showImage:function(){
            this.image=!this.image
            this.bigImageModal=this.bigImage
        },
       toggleP1:function(){
           this.bigImage=this.product1
       },
       toggleP2:function(){
           this.bigImage=this.product2
       },
       toggleP3:function(){
           this.bigImage=this.product3
       },
       toggleP4:function(){
           this.bigImage=this.product4
       },
        toggleModalP1:function(){
            if(this.mobile){
                this.bigImage=this.product1
            }
            else{
                this.bigImageModal=this.product1
            }
       },
       toggleModalP2:function(){
           if(this.mobile){
               this.bigImage=this.product2
            }
            else{
                this.bigImageModal=this.product2
            }
       },
       toggleModalP3:function(){
           if(this.mobile){
               this.bigImage=this.product3
            }
            else{
                this.bigImageModal=this.product3
            }
       },
       toggleModalP4:function(){
           if(this.mobile){
               this.bigImage=this.product4
            }
            else{
                this.bigImageModal=this.product4
            }
       },
       nextToggle:function(){
           switch (this.bigImageModal) {
               case this.product1:
                   this.toggleModalP2();
                   this.OverlayM2();
                   break;
                case this.product2 :
                    this.toggleModalP3();
                    this.OverlayM3();
                    break;
                case this.product3 :
                    this.toggleModalP4();
                    this.OverlayM4();
                    break;
                case this.product4 :
                    this.toggleModalP1();
                    this.OverlayM1();
                    break;
               default:
                   this.bigImageModal="image-product-1.jpg";
                   break;
           }
       },
       nextToggleMobile:function(){
           switch (this.bigImage) {
               case this.product1:
                   this.toggleModalP2();
                   break;
                case this.product2 :
                    this.toggleModalP3();
                    break;
                case this.product3 :
                    this.toggleModalP4();
                    break;
                case this.product4 :
                    this.toggleModalP1();
                    break;
               default:
                   this.bigImage="image-product-1.jpg";
                   break;
           }
       },
       previousToggle:function(){
            switch (this.bigImageModal) {
                case this.product1:
                    this.toggleModalP4();
                    this.OverlayM4();
                    break;
                case this.product2 :
                    this.toggleModalP1();
                    this.OverlayM1();
                    break;
                case this.product3 :
                    this.toggleModalP2();
                    this.OverlayM2();
                    break;
                case this.product4 :
                    this.toggleModalP3();
                    this.OverlayM3();
                    break;
                default:
                    this.bigImageModal="image-product-1.jpg";
                    break;
            }
       },
       previousToggleMobile:function(){
            switch (this.bigImage) {
                case this.product1:
                    this.toggleModalP4();
                    break;
                case this.product2 :
                    this.toggleModalP1();
                    break;
                case this.product3 :
                    this.toggleModalP2();
                    break;
                case this.product4 :
                    this.toggleModalP3();
                    break;
                default:
                    this.bigImage="image-product-1.jpg";
                    break;
            }
       },
       Overlay1:function(){
           this.$refs.thumbnail1.classList.add("defaultO")
           this.$refs.thumbnail2.classList.remove("defaultO")
           this.$refs.thumbnail3.classList.remove("defaultO")
           this.$refs.thumbnail4.classList.remove("defaultO")
        },
       Overlay2:function(){
           this.$refs.thumbnail2.classList.add("defaultO")
           this.$refs.thumbnail1.classList.remove("defaultO")
           this.$refs.thumbnail3.classList.remove("defaultO")
           this.$refs.thumbnail4.classList.remove("defaultO")
        },
       Overlay3:function(){
           this.$refs.thumbnail3.classList.add("defaultO")
           this.$refs.thumbnail2.classList.remove("defaultO")
           this.$refs.thumbnail1.classList.remove("defaultO")
           this.$refs.thumbnail4.classList.remove("defaultO")
        },
       Overlay4:function(){
           this.$refs.thumbnail4.classList.add("defaultO")
           this.$refs.thumbnail2.classList.remove("defaultO")
           this.$refs.thumbnail3.classList.remove("defaultO")
           this.$refs.thumbnail1.classList.remove("defaultO")
        },
       OverlayM1:function(){
           this.$refs.thumbnailM1.classList.add("defaultO")
           this.$refs.thumbnailM2.classList.remove("defaultO")
           this.$refs.thumbnailM3.classList.remove("defaultO")
           this.$refs.thumbnailM4.classList.remove("defaultO")
        },
       OverlayM2:function(){
           this.$refs.thumbnailM2.classList.add("defaultO")
           this.$refs.thumbnailM1.classList.remove("defaultO")
           this.$refs.thumbnailM3.classList.remove("defaultO")
           this.$refs.thumbnailM4.classList.remove("defaultO")
        },
       OverlayM3:function(){
           this.$refs.thumbnailM3.classList.add("defaultO")
           this.$refs.thumbnailM2.classList.remove("defaultO")
           this.$refs.thumbnailM1.classList.remove("defaultO")
           this.$refs.thumbnailM4.classList.remove("defaultO")
        },
       OverlayM4:function(){
           this.$refs.thumbnailM4.classList.add("defaultO")
           this.$refs.thumbnailM2.classList.remove("defaultO")
           this.$refs.thumbnailM3.classList.remove("defaultO")
           this.$refs.thumbnailM1.classList.remove("defaultO")
        },
    }
}
</script>

<style lang="scss" scoped>
    .imageWrapper{
        margin-top: 5rem;
        display: grid;
        grid-template-rows: 1fr auto auto;
        grid-row-gap: 1.2rem;
        place-items: center;
        @media (max-width:750px) {
            margin-top:0;
            position: relative;
        }
        img{
            width:100%;
            border-radius:0px;
            height: auto;
            object-fit: cover;
        }
        .toggleLeft{
            display: grid;
            place-items: center;
            justify-self: start;
            height: 2rem;
            width: 2rem;
            border-radius: 19px;
            background-color: white;
            position: absolute;
            left: 5%;
            cursor: pointer;
                &:hover,&:active{
                svg{
                    path{
                        stroke: hsl(26, 100%, 55%);
                    }
                }
            }
        }
        .toggleRight{
            justify-self: end;
            display: grid;
            place-items: center;
            height: 2rem;
            width: 2rem;
            border-radius: 19px;
            background-color: white;
            position: absolute;
            right: 5%;
            cursor: pointer;
            &:hover,&:active{
                svg path{
                        stroke: hsl(26, 100%, 55%);
                }

            }
        }
        .currentImage {
            display: grid;
            place-items: center;
            img{
                width:60%;
                border-radius:10px;
                height: auto;
                object-fit: cover;
                cursor: pointer;
                @media (max-width:750px) {
                    width: 100%;
                    border-radius:0;
                    pointer-events: none;
                }
            }
        }
        .bottomImage{
            display: grid;
            grid-template-columns: repeat(4,1fr);
            grid-column-gap: 1rem;
            width: 60%;
            .overlay{
                width: 100%;
                height: 100%;
                img{
                    width:100%;
                    height:100%;
                    object-fit: cover;
                    border-radius:5px;
                    cursor: pointer;
                }
                 &:hover{
                    border-radius:7.5px;
                    position: relative;
                    cursor: pointer;
                    &::after{
                        content: '';
                        position: absolute;
                        top: 0;
                        left: 0;
                        width: 100%;
                        height: 100%;
                        background-color: rgba($color: #ffff, $alpha: .5);
                        border-radius: 5px;
                    }
                }
            }
            .defaultO{
                border: 2px solid hsl(26, 100%, 55%);
                border-radius:7.5px;
                position: relative;
                    &::after{
                        content: '';
                        position: absolute;
                        top: 0;
                        left: 0;
                        width: 100%;
                        height: 100%;
                        background-color: rgba($color: #ffff, $alpha: .5);
                        border-radius: 5px;
                    }
            }
        }
    }
    .modal{
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        width: 100%;
        height: 100%;
        display: grid;
        place-items: center;
        z-index: 1;
        .modalOverlay{
            position: fixed;
            top: 0;
            bottom: 0;
            left: 0;
            right: 0;
            width: 100%;
            height: 100%;
            background-color: rgba($color: #000000, $alpha: .5);
        }
        .modalContent{
            position: absolute;
            @media (min-width:950px) {
                top:2.5rem;
            }
            top:1rem;
            width: 50%;
            height:400px;
            display: grid;
            grid-template-rows: 1fr auto;
            grid-row-gap: 1.2rem;
            place-items: center;
            .modalCurrentImage{
                display: grid;
                position: relative;
                .toggleLeft{
                    display: grid;
                    place-items: center;
                    justify-self: start;
                    height: 2rem;
                    width: 2rem;
                    border-radius: 19px;
                    background-color: white;
                    position: absolute;
                    left: 16%;
                    cursor: pointer;
                     &:hover,&:active{
                        svg{
                            path{
                                stroke: hsl(26, 100%, 55%);
                            }
                        }
                    }
                }
                .toggleRight{
                    justify-self: end;
                    display: grid;
                    place-items: center;
                    height: 2rem;
                    width: 2rem;
                    border-radius: 19px;
                    background-color: white;
                    position: absolute;
                    right: 16%;
                    cursor: pointer;
                    &:hover,&:active{
                        svg path{
                                stroke: hsl(26, 100%, 55%);
                        }

                    }
                }
            }
            .modalBottomImage{
                     width: 55%;
            }
            .close{
                position: absolute;
                right: 20%;
                top: 0%;
                cursor: pointer;
                @media (min-width:950px) {
                    top: -1.5rem;
                }
                svg path{
                    fill: white;
                }
                &:hover,&:active{
                    svg path{
                    fill:hsl(26, 100%, 55%);
                }
                }
            }
        }
    }
</style>