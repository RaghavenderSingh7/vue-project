<script setup lang="ts">
import { onMounted, ref } from 'vue'
import ShopContext from '../components/ShopContext.vue'
import ProductCard from '../components/ProductCard.vue';
// import ProductCard from '../components/ProductCard.vue'
const show = ref(false)
const categories = ref([])
const products = ref([])
const activeCategory = ref(null)
const onShow = () => {
  show.value = !show.value
}
const fetchCategory = async () => {
  try {
    const response = await fetch('https://fakestoreapi.com/products/categories')
    const jsonData = await response.json()
    categories.value = jsonData
    console.log(categories.value)
  } catch (error) {
    console.log(error)
  }
  const fetchProduct = async () => {
  try {
    const response = await fetch('https://fakestoreapi.com/products');
    const jsonData = await response.json()
    products.value = jsonData
    console.log(products.value)
  } catch (error) {
    console.log(error)
  }
  onMounted(() => {
    fetchCategory()
  })
  onMounted(() => {
    fetchProduct()
  })
}
</script>

<template>
  <div class="filterWrapper">
    Home Page
    <div class="topFlex">
      <div
      :class="activeCategory === item ? 'activeCategory':''"
        @click="activeCategory = activeCategory === item ? '' : 'item'"
        v-for="item in category"
        :key="item.id"
        class="category"
      >
        {{ item }}
      </div>
    </div>
    <div class="box">
      <div class="badge">
        <svg
          @click="onShow"
          viewBox="0 0 24 24"
          width="24"
          height="24"
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
        <ShopContext @on-go-basket="show = false" v-if="show" />
      </div>
    </div>
  </div>
  <div class="bottomFlex">
    <ProductCard v-for="item in products" :key="item.id" :item = 'item'/>
  </div>
</template>
<style scoped>
.filterWrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
  flex-wrap: wrap;
}
.topFlex {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
}
.category {
  cursor: pointer;
  padding: 4px 16px;
  background-color: whitesmoke;
  border: 1px solid grey;
  font-size: 12px;
  font-weight: 500px;
  border-radius: 16px;
  margin-top: 8px;
}
.activeCategory {
  border: 1px solid red;
  background: red;
  color: whitesmoke;
  font-weight: 600;
}
.box {
  position: relative;
  cursor: pointer;
  color: darkslategray;
  transition: all 0.5s;
}
.box:hover {
  color: lightskyblue;
}
.badge {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: -8px;
  right: -8px;
  font-size: 12px;
  background-color: lightskyblue;
  border-radius: 100%;
  color: whitesmoke;
  width: 16px;
  height: 16px;
}
</style>
