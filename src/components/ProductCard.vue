<template>
  <div class="productCard">
    <div class="box">
      <svg
        viewBox="0 0 24 24"
        width="16"
        height="16"
        stroke="currentColor"
        stroke-width="2"
        fill="none"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="css-i6dzq1"
      >
        <circle cx="9" cy="21" r="1"></circle>
        <circle cx="20" cy="21" r="1"></circle>
        <path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"></path>
      </svg>
    </div>
    <div class="cardImage"></div>
    <div class="desc">
      <div class="btn">Detail</div>
      <span>Title</span>
      <div class="price">15$</div>
    </div>
  </div>
</template>

<script setup lang="ts">
import defineProps from 'vue'
 const {item} = defineProps(['item'])
</script>

<style scoped>
.productCard {
  position: relative;
  overflow: hidden;
  cursor: pointer;
  width: 250px;
  background-color: whitesmoke;
  border: 1px solid grey;
  border-radius: 20px;
}
.cardImage {
  width: 100%;
  object-fit: fill;
  margin-bottom: 16px;
}
.cardImage img {
  width: 100%;
  height: 250px;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
}
.desc {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  color: grey;
  font-size: 12px;
  font-weight: 500;
  padding: 8px;
  position: relative;
  max-height: 60px;
}
.price {
  margin-top: 4px;
  color: blue;
  font-size: 24px;
  font-weight: 500;
}
.btn {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  transition: all 0.4s ease;
  background-color: blue;
  color: whitesmoke;
  font-size: 12px;
  font-weight: 500;
  transform: translateY(100px);
}
.productCard:hover > .desc > .btn {
  transform: translateY(0);
}
.box{
    width: 24px;
    height:24px;
    position: absolute;
    background-color: 1px solid orange;
    border-radius: 100%;
    top: 8px;
    right: 8px;
    display: flex;
    justify-content: center;
    align-items: center;
  
}
</style>
