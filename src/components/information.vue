<template>
  <div class="textContent">
      <p class="compagny">Sneaker Company</p>
      <h1 class="fall">Fall Limited Edition Sneakers</h1>
      <p class="description">
          These low-profile sneakers are your perfect casual wear companion. Featuring a 
          durable rubber outer sole, they’ll withstand everything the weather can offer.
      </p>
      <div class="prices">
          <p class="price">${{price}}</p>
          <div class="reduction">
              <p>{{reduction}}%</p>
          </div>
          <p class="priceCrossed">${{priceCrossed}}</p>
      </div>
      <div class="addCart">
          <div class="add">
              <svg v-on:click="decreaseProduct" width="12" height="4" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><path d="M11.357 3.332A.641.641 0 0 0 12 2.69V.643A.641.641 0 0 0 11.357 0H.643A.641.641 0 0 0 0 .643v2.046c0 .357.287.643.643.643h10.714Z" id="a"/></defs><use fill="#FF7E1B" fill-rule="nonzero" xlink:href="#a"/></svg>
              <p class="numberOf">{{numberOf}}</p>
              <svg v-on:click="increaseProduct" width="12" height="12" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><path d="M12 7.023V4.977a.641.641 0 0 0-.643-.643h-3.69V.643A.641.641 0 0 0 7.022 0H4.977a.641.641 0 0 0-.643.643v3.69H.643A.641.641 0 0 0 0 4.978v2.046c0 .356.287.643.643.643h3.69v3.691c0 .356.288.643.644.643h2.046a.641.641 0 0 0 .643-.643v-3.69h3.691A.641.641 0 0 0 12 7.022Z" id="b"/></defs><use fill="#FF7E1B" fill-rule="nonzero" xlink:href="#b"/></svg>
          </div>
          <div class="buttonAdd">
              <img src="../../images/cartWhite.svg" alt=" ">
              <p>Add to cart</p>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name:'information',
    data(){
        return{
            price:null,
            reduction:50,
            priceCrossed:250.00,
            numberOf:0,
        }
    },
    props:{
        mobile:Boolean,
    },
    created(){
        this.Price();
    },
    methods:{
        increaseProduct:function(){
            this.numberOf=this.numberOf+1
        },
        decreaseProduct:function(){
            if (this.numberOf>0) {
                this.numberOf=this.numberOf-1
            }
        },
        Price:function(){
            this.price=this.priceCrossed*(this.reduction/100)
        }
    }
}
</script>

<style lang="scss" scoped>
    .textContent{
        padding-top: 6rem;
        @media (max-width:750px) {
            padding-top:0;
            padding-left: 2rem;
        }
        .compagny{
            font-size: 16px;
            font-weight: bold;
            color: hsl(26, 100%, 55%);
            padding-bottom: .5rem;
        }
        .fall{
            width: 70%;
            padding-bottom: 1rem;
            @media (max-width:750px) {
                width: 80%;
            }
        }
        .description{
            font-size: 15px;
            padding-bottom: 1rem;
            width: 75%;
            text-align:justify;
            @media (max-width:750px) {
                width: 85%;
            }
        }
        .prices{
            width: 23%;
            display: grid;
            grid-template-columns: 1fr auto;
            margin-bottom: 1rem;
            @media (max-width:750px) {
                width: 90%;
                grid-template-columns: auto 1fr 1fr;
            }
            .price{
                font-weight: bold;
                font-size: 20px;
                @media (max-width:750px) {
                    font-size:30px;
                    align-self: center;
                    justify-self: start;
                }
            }
            .reduction{
                display: grid;
                place-items: center;
                height: 90%;
                border-radius: 3px;
                background-color: hsl(25, 100%, 94%);
                @media (max-width:750px) {
                    min-width: 50%;
                    max-width: 60%;
                    margin-left: 1rem;
                }
                p{
                    font-weight: bold;
                    font-size: 90%;
                    color: hsl(26, 100%, 55%);
                    padding: 10%;

                }
            }
            .priceCrossed{
                font-size: 85%;
                font-weight: bold;
                color: hsl(220, 14%, 75%);
                text-decoration-line: line-through;
                @media (max-width:750px) {
                    font-size:20px;
                    align-self: center;
                    justify-self: start;
                }
            }
        }
        .addCart{
            width: 75%;
            height: 2rem;
            display: grid;
            grid-template-columns: auto auto;
            grid-column-gap: 1rem;
            @media (max-width:750px) {
                grid-template-rows:1fr 1fr;
                grid-template-columns:initial;
                grid-row-gap: 1rem;
                width: 90%;
                height: 6rem;
            }
            .add{
                display: grid;
                grid-template-columns: repeat(3,auto);
                place-items: center;
                background-color: hsl(223, 64%, 98%);
                border-radius: 3px;
                p{
                    font-weight: bold;
                    cursor: pointer;
                }
                svg{
                    cursor: pointer;
                }
            }
            .buttonAdd{
                display: grid;
                grid-template-columns: auto 1fr;
                place-items: center;
                background-color: hsl(26, 100%, 55%);
                border-radius: 5px;
                position: relative;
                cursor: pointer;
                &:hover{
                    opacity: .5;
                }
                img{
                    height: auto;
                    object-fit: cover;
                    position: absolute;
                    left: .3rem;
                }
                p{
                    color: white;
                    position: absolute;
                    right: 1rem;
                }
            }
        }
    }
</style>