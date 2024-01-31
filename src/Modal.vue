<template>
  <div class="black-bg" v-if="opening == true">
  <div class="white-bg">
    <img :src="onerooms[clicks].image" class="room-img"/>
    <h4>{{ onerooms[clicks].title }}</h4>
    <p>{{onerooms[clicks].content}}</p>
    <input v-model.number="month">
    <!-- @input="month = $event.target.value" -->
    <p> {{month}}개월 선택함 {{onerooms[clicks].price * month}}원</p>
    <button @click='$emit("closeModal")'>닫기</button>
  </div>
</div>
</template>

<script>
export default {
    name : 'ModalItem',
    data(){
      return {
        month : 1,
      }
    },
    watch : {
      month(a){
        if (a > 13){
          alert('too big')
          this.month = 1
          
        }
        if (isNaN(a) == true){
          alert('nono')
          this.month = 1

        }
      },

    },
    props : {
        onerooms : Array,
        clicks : Number,
        opening : Boolean,

        
    }
}
</script>

<style>

</style>