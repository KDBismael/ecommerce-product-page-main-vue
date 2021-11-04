<template>
  <div class="headerWrapper">
      <div class="header">
            <div v-if="mobile" class="burger">
                <img v-on:click="showNav" src="../../images/icon-menu.svg" alt="menu-icon">
            </div>
            <div class="logo">
                <img src="../../images/logo.svg" alt="logo">
            </div>
            <nav v-if="!mobile">
                <ul>
                    <router-link to="#">Collections</router-link>
                    <router-link to="#">Men</router-link>
                    <router-link to="#">Women</router-link>
                    <router-link to="#">About</router-link>
                    <router-link to="#">Contact</router-link>
                </ul>
            </nav>
            <div class="cart">
                <div v-on:click="openCart" class="iconCart">
                    <img src="../../images/icon-cart.svg" alt="cart">
                </div>
                <div class="image">
                    <img src="../../images/image-avatar.png" alt=" avatar">
                </div>
            </div>
        </div>
        <div v-if="mobileNav" class="modal">
            <div v-on:click="closeNav" class="overlay"></div>
            <div class="mobileNav" :class="{'open':openNav}">
                <img v-on:click="closeNav" src="../../images/icon-close.svg" alt="close">
                <nav>
                     <ul>
                        <router-link class="Collections" to="#">Collections</router-link>
                        <router-link to="#">Men</router-link>
                        <router-link to="#">Women</router-link>
                        <router-link to="#">About</router-link>
                        <router-link to="#">Contact</router-link>
                    </ul>
                </nav>
            </div>
        </div>
        <div v-if="cart" class="cartModal">
            <div v-on:click="openCart" class="overlay"></div>
            <div class="cartContent">
                <div class="name">
                    <h1>cart</h1>
                </div>
                <div class="section">
                    <div v-if="false" class="empty">
                        <p>Your cart is empty.</p>
                    </div>
                    <div v-if="true" class="fill">
                        <div class="description">
                            <img src="../../images/image-product-1-thumbnail.jpg" alt=" product">
                            <div class="info">
                                <div class="text">
                                    <p class="title">Fall Limited Edition Sneakers</p>
                                    <div class="prices">
                                        <p class="price">$125 x 3</p>
                                        <p class="result">$375</p>
                                    </div>
                                </div>
                                <img src="../../images/icon-delete.svg" alt=" ">
                            </div>
                        </div>
                        <div class="checkout">
                            <div class="btn">
                                Checkout
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
  </div>
</template>

<script>
export default {
    name:'Header',
    props:{
        mobile:Boolean,
    },
    data(){
        return{
            mobileNav:false,
            openNav:false,
            cart:false
        }
    },
    methods:{
        openMenu:function(){
            this.openNav=!this.openNav
        },
        closeMenu:function(){
            this.mobileNav=!this.mobileNav;
        },
        showNav:function(){
            this.mobileNav=!this.mobileNav;
            setTimeout(this.openMenu,100);
        },
        closeNav:function(){
            setTimeout(this.openMenu,5);
            setTimeout(this.closeMenu,800);
        },
        openCart:function(){
            this.cart=!this.cart
        }
    }
}
</script>

<style lang="scss" scoped>
    .cartModal{
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        display: grid;
        z-index: 2;
        .overlay{
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }
        .cartContent{
            position: absolute;
            margin-top: 4rem;
            margin-right: 1rem;
            width: 30%;
            height: 160px;
            justify-self: end;
            display: grid;
            grid-template-rows: auto 1fr;
            background-color: white;
            border-radius: 5px;
            box-shadow: 1px 3px 10px  hsl(220, 14%, 75%);
            .name{
                height: 2.5rem;
                display: grid;
                border-bottom: 1px solid hsl(220, 11%, 89%);
                h1{
                    font-size: 15px;
                    padding-left: 1rem;
                    align-self: center;
                }
            }
            .section{
                .empty{
                    width: 100%;
                    height: 100%;
                    display: grid;
                    place-items: center;
                }
                .fill{
                    width: 100%;
                    height: 100%;
                    display: grid;
                    grid-template-rows: 1fr 1fr;
                    .description{
                        display: grid;
                        grid-template-columns: 1fr auto;
                        margin-top: 1rem;
                        img{
                            width: 80%;
                            height: auto;
                            object-fit: cover;
                            object-position: right;
                            border-radius: 5px;
                            margin-left: .5rem;
                        }
                        .info{
                            grid-column: 2/3;
                            display: grid;
                            grid-template-columns: auto 1fr;
                            .text{
                                margin-left: .5rem;
                                .title{
                                    font-size: 75%;
                                }
                                .prices{
                                    font-size: 15px;
                                    display: grid;
                                    grid-template-columns: 1fr 1fr;
                                    .result{
                                        font-weight: bold;
                                        font-size: 15px;
                                    }
                                }
                            }
                            img{
                                width: 70%;
                                margin-top: .8rem;
                                cursor: pointer;
                                margin-right: .5rem;
                                margin-left:0;
                            }
                        }
                    }
                    .checkout{
                        width: 100%;
                        display: grid;
                        place-items: center;
                        .btn{
                            display: grid;
                            place-items: center;
                            width: 90%;
                            height: 60%;
                            border-radius: 8px;
                            color: white;
                            background-color: hsl(26, 100%, 55%);
                            cursor: pointer;
                            &:hover{
                                opacity: .5;
                            }
                        }
                    }
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
        .overlay{
            position: fixed;
            top: 0;
            bottom: 0;
            left: 0;
            right: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 1;
        }
        .open{
            transform:none !important;
        }
        .mobileNav{
            transition: 1s transform cubic-bezier(0,.12,.14,1);
            transform: translateX(-100%);
            position: absolute;
            padding-top: 1.5rem;
            width: 70%;
            height: 100%;
            background-color: white;
            z-index: 2;
            display: grid;
            grid-template-rows: auto 1fr;
            img{
                margin: 1rem;
                cursor: pointer;
            }
            nav{
                display: grid;
                ul{
                    padding-top: 1.5rem;
                    padding-left: 1rem;
                    align-self: start;
                    display: grid;
                    grid-template-rows: repeat(5,auto);
                    grid-row-gap: 1rem;
                    a{
                        text-decoration: none;
                        font-weight: bold;
                        color:black;
                    }
                }
            }
        }
    }
    .headerWrapper{
        display: grid;
        place-items: center;
    }
    .header{
        width: 80%;
        height: 4rem;
        display: grid;
        grid-template-columns: auto 1fr auto;
        @media (max-width:750px) {
            grid-template-columns: auto auto 1fr;
            width: 90%;
        }
        @media (min-width:751px) {
            border-bottom: 1px solid hsl(223, 20%, 93%);
            border-radius:.5px ;
        }
        .burger{
            height: 1rem;
            place-self: center;
            padding-right: .5rem;
            img{
                cursor: pointer;
                height: .8rem;
            }
        }
        .logo{ 
            display: grid;
            height: 4rem;
            place-items: center;
            img{
                cursor: pointer;
                width: 90%;
                height: 1rem;
                align-self: center;
            }
        }
        nav{
            display: grid;
            height: 4rem;
            place-items: center;
            ul{
                display: grid;
                grid-template-columns: repeat(5,auto);
                grid-column-gap: 1rem;
                padding-left: 1rem;
                justify-self: start;
                a{
                    text-decoration: none;
                    font-size: clamp(13px,14px,16px);
                    color: hsl(220, 14%, 75%);
                    position: relative;
                   &:hover{
                        &::after{
                            content: '';
                            border-bottom: 2px solid hsl(26, 100%, 55%);
                            position: absolute;
                            width:100%;
                            left:0;
                            top: 2.45rem;
                        }
                   }
                }
            }
        }
        .cart{
            display: grid;
            place-items: center;
            grid-template-columns: repeat(2,auto);
            grid-column-gap: 1.5rem;
            @media (max-width:750px) {
                grid-column-gap: 0rem;
                place-self: end;
            }
            height: 4rem;
            .iconCart{
                justify-self: end;
                cursor: pointer;
            }
            .image{
                @media (max-width:750px) {
                    justify-self: start;
                    padding-left: 1rem;
                }
            }
            .image img{
                cursor: pointer;
                width: 40px;
                height: 40px;
                @media (max-width:750px) {
                    width: 25px;
                    height: 25px;
                }
                object-fit: cover;
                &:hover{
                    border: 1px solid hsl(26, 100%, 55%);
                    border-radius:50px;
                }
            }
        }
    }
</style>