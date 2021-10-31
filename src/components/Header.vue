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
                <div class="iconCart">
                    <img src="../../images/icon-cart.svg" alt="cart">
                </div>
                <div class="image">
                    <img src="../../images/image-avatar.png" alt=" avatar">
                </div>
            </div>
        </div>
        <div v-if="mobileNav" class="modal">
            <div class="overlay"></div>
            <div class="mobileNav" :class="{openNav:mobileNav}">
                <img v-on:click="showNav" src="../../images/icon-close.svg" alt="close">
                <nav>
                     <ul>
                        <router-link to="#">Collections</router-link>
                        <router-link to="#">Men</router-link>
                        <router-link to="#">Women</router-link>
                        <router-link to="#">About</router-link>
                        <router-link to="#">Contact</router-link>
                    </ul>
                </nav>
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
            openNav:null
        }
    },
    methods:{

        showNav:function(){
            this.mobileNav=!this.mobileNav
        }
    }
}
</script>

<style lang="scss" scoped>
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
            // transform: translateX(-200px);
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
            }
            .image{
                @media (max-width:750px) {
                    justify-self: start;
                    padding-left: 1rem;
                }
            }
            .image img{
                width: 40px;
                height: 40px;
                @media (max-width:750px) {
                    width: 25px;
                    height: 25px;
                }
                object-fit: cover;
            }
        }
    }
</style>