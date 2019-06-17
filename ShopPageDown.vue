<template>
    <div class="container">
        <div class="separation_line"></div>
        <p>Detail</p>
        <div class="introduction">
            <img v-bind:src="products[0].detail">
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
    display: flex;
    flex-direction: column;
    align-items: center;
}

.separation_line{
    background: #f88e7b;
    width: 100%;
    height: 7vh;
    margin-bottom: 2vh;
}

.introduction{
    position: relative;
    border: #f88e7b 1px solid;
    width: 640px;
    height: 4057px;
    margin-bottom: 10vh;
}

p{
    font-size: 2rem;
}

.introduction img{
	position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    margin: auto;
    max-width: 100%;
    max-height: 100%;
}

@media screen and (max-width: 400px){
.introduction{
    border: #f88e7b 1px solid;
    width: 80vw;
    height: 1500px;
    margin-bottom: 10vh;
}

p{
    font-size: 1.2rem;
}

.separation_line{
    background: #f88e7b;
    width: 100%;
    height: 5vh;
    margin-bottom: 0;
}
}
</style>
