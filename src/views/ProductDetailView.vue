<template>
  <div class="productDetailCard">
    <div class="imageSection">
      <img :src="detail.image" />
    </div>
    <div class="productInfoSection">
      <div class="title">Product Number#{{ router.params.id }}</div>
      <div class="title">{{ detail.title }}</div>
      <div class="desc">{{ detail.desc }}</div>
      <div class="price">{{ detail.price }}$</div>
      <div class="rate">
        <!-- v-for="item in 5" -->
        <svg
          viewBox="0 0 24 24"
          width="16"
          height="16"
          :stroke="Math.floor(detail.rating.rate)>=item ? '#1874ff': 'currentColor'"
          stroke-width="2"
          :fill="Math.floor(detail.rating.rate)>= item ? '#1874ff': 'none'"
          stroke-linecap="round"
          stroke-linejoin="round"
          class="css-i6dzq1"
        >
          <polygon
            points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"
          ></polygon>
        </svg>
        {{ detail.rate.count }} Vote
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'

const router = useRoute()
const detail = ref({
  category: ' ',
  description: ' ',
  id: ' ',
  image: ' ',
  title: ' ',
  price: ' ',
  rating: { rate: 0, count: 0 }
})
const getProductById = () => {
  fetch('https://fakestoreapi.com/products/' + router.params.id)
    .then((res) => res.json())
    .then((json) => (detail.value = json))
}
onMounted(getProductById)
</script>

<style scoped>
.productDetailCard {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  padding: 20px;
  width: 100%;
  background-color: whitesmoke;
  border: 1px solid grey;
  border-radius: 20px;
}
.imageSection {
  margin-right: 32px;
}
.imageSection img {
  width: 150px;
}
.productInfoSection {
  display: flex;
  flex: 1%;
  flex-direction: column;
  align-items: center;
}
.title {
  width: 100%;
  text-align: center;
  color: grey;
  font-size: 32px;
  font-weight: 500;
  margin-bottom: 8px;
}
.desc {
  margin-top: 8px;
  color: grey;
  font-size: 24px;
  font-weight: 500;
}
.price {
  margin-top: 8px;
  color: blue;
  font-size: 24px;
  font-weight: 500;
}
.rate {
  color: grey;
  display: flex;
  gap: 8px;
}
</style>
