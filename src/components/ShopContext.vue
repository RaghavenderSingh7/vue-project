<script lang="ts">
import { defineEmits, defineProps } from 'vue';
const {item} = defineProps(['item'])
const emit = defineEmits(["onGoBasket"]);
const goBasket = (): void => {
  emit("onGoBasket");
};
</script>
<template>
  <div class="contextWrapper">
    <div v-for="data in item" :key="data.id" class="contextItem">
      <div class="image">
        <img :src="data.img" alt="" />
      </div>
      <div class="content">
        <div class="title">{{data.title}}</div>
        <div class="price">{{data.price}}$</div>
      </div>
    </div>
    <div @click="goBasket" class="contextItem completeBox">complete the shopping</div>
  </div>
</template>

<style scoped>
.contextWrapper{
    z-index: 10;
    position:absolute;
    background-color: whitesmoke;
    right: 0;
    border: 1px solid grey;
    padding-top: 8px;
    padding-bottom: 8px;
    border-radius: 10px;
    max-width: 600px;
    min-width: 250px;
    filter: drop-shadow(0px 8px 12px rgba(0 ,0 ,0 ,0.15));
}
.contextItem{
   display: flex;
   padding-left: 16px;
   padding-right: 16px;
   border-bottom: 1px solid grey;
}
.image {
 margin-right: 12px;
}
.image img{
    width: 50px;
    height: 50px;
    object-fit: fill;
}
.content {
    font-weight: 500;
    display: flex;
    flex-direction: column;
}
.price{
    margin-top: 4px;
    color: blue;
}
.title{
    font-size: 20px;
    font-weight: 600;
    color: black !important;
}
.completeBox{
    display: flex;
    justify-content: center;
    align-items: center;
    border-top: 1px solid grey;
    padding: 16px 0px;
    color: blue;
}
</style>
