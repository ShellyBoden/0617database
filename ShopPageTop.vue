<template>
<div class="container">
    <div class="big_pic"><img v-bind:src="products[0].picurl"></div>
    <div class="right_content">
        <div class="text">{{products[0].name}}</div>
        <div class="price">{{products[0].price}}</div>
        <div class="quantity_ar">
        <label class="quantity">數量：</label><input type="number" value="1" min="1" max="99" class="no-spinners">
            <img id="add" src="../assets/add.png"><img id="remove" src="../assets/remove.png">
        </div>
        <div class="btn">
            <button>加入購物車</button><button>加入最愛</button>
        </div>
    </div>
</div>
</template>

<script>
import { fb,db } from "../firebase/index";

export default {
  data(){
    return {
        products: [],
        product: {
          name:null,
          price:null,
          picurl:null,
          detail:null
        }
    }
  },
  firestore(){
      return {
        products: db.collection('ShopList')
      }
  }
};
</script>


<style scoped>

.container{
    padding: 5vw;
    display: flex;
    align-items:center;
}

.big_pic{
    position: relative;
    width:40vw;
    height: 80vh;
}

.right_content{
    text-align: left;
    line-height: 5vw;
    margin-left: 10vw;
    font-size: 1.5rem;
}

input{
    width:3vw;
    height:3vw;
    margin:0.5vw;
    text-align: center;
    font-size: 1.5rem;
}

#remove,#add{
    width:3vw;
    margin: 0.5vw;
}

.quantity_ar{
    display: flex;
    align-items:center;
}

.text{
    font-size: 2.5rem;
    margin-bottom: 3vh;
}

button{
    font-family: '微軟正黑體';
    font-size: 1.5rem;
    height: 8vh;
    margin-top: 7vh;
    margin-right: 1vw;
    width: 15vw;
}

.btn{
    display: flex;
}

.big_pic img {
	position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    margin: auto;
    max-width: 100%;
    max-height: 100%;
}

/* ----------------隱藏內建的增加減少鍵---------------- */
.no-spinners {
  -moz-appearance:textfield;
}

.no-spinners::-webkit-outer-spin-button,
.no-spinners::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
/* ----------------隱藏內建的增加減少鍵---------------- */

/*-----------------------------------------rwd-----------------------------------------*/
@media screen and (max-width: 400px){
.container{
    padding: 5vw;
    display: flex;
    flex-direction: column;
    align-items:flex-start;
}

.big_pic{
    width:100%;
    height: 60vh;
    margin-bottom: 5vh;
}

.right_content{
    margin: 0px;
    font-size: 1rem;
}

input{
    font-size: 1rem;
    width: 10vw;
    height: 5vh;
}

#remove,#add{
    width: 5vw;
    margin: 2vw;
}

.quantity_ar{
    margin-top: 5vw;
    margin-bottom: 5vw;
}

.text{
    font-size: 1.5rem;
    margin-bottom: 8vw;
}

button{
    width:40vw;
    font-size: 1rem;
    margin-top:0;
}

.btn{
    display: flex;
    /* margin-left: 2vw; */
    margin-top: 5vh;
}

/* ----------------隱藏內建的增加減少鍵---------------- */
.no-spinners {
  -moz-appearance:textfield;
}

.no-spinners::-webkit-outer-spin-button,
.no-spinners::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
/* ----------------隱藏內建的增加減少鍵---------------- */
}
</style>
