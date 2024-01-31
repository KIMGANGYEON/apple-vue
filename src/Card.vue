<template>
  

  <div>
    <img :src="onerooms.image" class="room-img">
    <h4 @click="$emit('openModal', onerooms.id)">{{ onerooms.title }}</h4>
    <p>{{ onerooms.price }}원</p>
  </div>


  <!-- <div v-for="(a, i) in onerooms" :key="i">
    <img :src="a.image" class="room-img">
    <h4 @click="opening = true; clicks = i">{{ onerooms[i].title }}</h4>
    <p>{{ onerooms[i].title }}</p>
    <p>{{ onerooms[i].price }}원</p>
  </div> -->
 
</template>

<script>
export default {
    name : 'CardItem',
    props : {
        onerooms : Object,
        // clicks : Number,
        // count : Number

    }
}
</script>

<style>

</style>