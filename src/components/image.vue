<template>
  <div class="imageWrapper">
      <div class="currentImage">
            <img v-on:click="showImage" :src="require('../../images/'+bigImage)" alt="product">
      </div>
      <div class="bottomImage">
          <div v-on:click=" toggleP1" class="overlay defaultO">
            <img class="thumbnail"  src="../../images/image-product-1-thumbnail.jpg" alt="product-th">
          </div>
          <div v-on:click=" toggleP2" class="overlay">
            <img class="thumbnail" src="../../images/image-product-2-thumbnail.jpg" alt="product-th">
          </div>
          <div v-on:click=" toggleP3" class="overlay">
            <img class="thumbnail" src="../../images/image-product-3-thumbnail.jpg" alt="product-th">
          </div>
          <div v-on:click=" toggleP4" class="overlay">
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
                    <div class="toggleLeft">
                        <svg width="12" height="18" xmlns="http://www.w3.org/2000/svg"><path d="M11 1 3 9l8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd"/></svg>
                    </div>
                    <img :src="require('../../images/'+bigImageModal)" alt="product">
                    <div class="toggleRight">
                        <svg width="13" height="18" xmlns="http://www.w3.org/2000/svg"><path d="m2 1 8 8-8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd"/></svg>
                    </div>
                </div>
                <div class="bottomImage modalBottomImage">
                    <div v-on:click=" toggleModalP1" class="overlay defaultO">
                        <img class="thumbnail"  src="../../images/image-product-1-thumbnail.jpg" alt="product-th">
                    </div>
                    <div v-on:click=" toggleModalP2" class="overlay">
                        <img class="thumbnail" src="../../images/image-product-2-thumbnail.jpg" alt="product-th">
                    </div>
                    <div v-on:click=" toggleModalP3" class="overlay">
                        <img class="thumbnail" src="../../images/image-product-3-thumbnail.jpg" alt="product-th">
                    </div>
                    <div v-on:click=" toggleModalP4" class="overlay">
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
           this.bigImageModal=this.product1
       },
       toggleModalP2:function(){
           this.bigImageModal=this.product2
       },
       toggleModalP3:function(){
           this.bigImageModal=this.product3
       },
       toggleModalP4:function(){
           this.bigImageModal=this.product4
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
        .currentImage {
            display: grid;
            place-items: center;
            img{
                width:60%;
                border-radius:10px;
                height: auto;
                object-fit: cover;
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