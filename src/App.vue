<template>



<transition name="fade">
  <Modal @closeModal='opening = false; clicks = $event' :onerooms='onerooms' :clicks="clicks" :opening='opening' />
</transition>

  <div class="menu">
    <a v-for="(HOme, i) in menus" :key="i">{{ HOme }}</a>
  </div>

  <Discount v-if="showDiscount == true"></Discount>

<!-- v-bind="obj" -->
  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>
  <!-- $event = 자식이 보낸 이벤트 -->
  <Card @openModal='opening = true; clicks = $event' :onerooms = "onerooms[i]" v-for = "(a ,i) in onerooms" :key="i"/>
  <button @click="count++">허위매물신고</button> <span>신고수 : {{ count}}</span>

  


  





  <!-- <div v-for="(a, i) in products" :key="i">
    <h4 :style="style">{{ a }}</h4>
    <p>{{ prices[i] }}만원</p>
     <h4 v-for="(Name, i) in products" :key="i">{{ Name }}</h4>
    <p v-for="(price, i) in prices" :key="i">{{price}}</p> -->
  <!-- </div> --> 
</template>

<script>

 import data from './oneroom.js';
 import DiscountItem from './Discount.vue'
 import Modaltem from './Modal.vue';
 import CardItem from './Card.vue';
// import func from 'vue-editor-bridge';




export default {
  name: 'App',
  data(){
    return{
      showDiscount : true,
      oneroomsorigin : [...data],
      // style : 'color : red',
      count : 0,
      obj : { name : 'kim', age : 20 },
      clicks : 0,
      onerooms : data,
      opening : false,
      // count : [0, 0, 0, 0, 0, 0],
      prices : [60, 70, 80],
      menus : ['home','Shop', 'About' ],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸']

    }
  },
  methods : {
    increase(){
      this.count++;
    },
    priceSort(){
      this.onerooms.sort(function(a,b){
        return a.price - b.price
      });
    },
    sortBack(){
      this.onerooms = [...this.oneroomsorigin]
    },
  },

  mounted(){
    setTimeout(() => {
      this.showDiscount = false;
    }, 10000)
  },

  components: {
    Discount : DiscountItem,
    Modal : Modaltem,
    Card : CardItem,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.discount {
  background: #eee;
  margin: 10px;
  padding: 20px;
  border-radius: 5px;
}

.menu{
  background: darkslateblue;
  padding: 30px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}

.room-img{
  width: 100%;
  margin-top: 40px;
}

.start {
  opacity: 0;
  transition: all 1s;
}

.end {
  opacity: 1;
}

.fade-enter-from {
  opacity: 0;
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
    transform: translateY(0px);

}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}


</style>
