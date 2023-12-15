<template>
  <div class="productDetailCard">
    <div class="imageSection">
      <img src="ff" alt="" />
    </div>
    <div class="productInfoSection">
      <div class="title">Product Number</div>
      <div class="title">Title</div>
      <div class="desc">Discription</div>
      <div class="price">13$</div>
      <div class="rate">
        <svg
          v-for="item in 5"
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
          <polygon
            points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"
          ></polygon>
        </svg>
        20votes
      </div>
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.productDetailCard{
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
.imageSection{
    margin-right: 32px;
}
.imageSection img{
    width: 150px;
}
.productInfoSection{
    display: flex;
    flex: 1%;
    flex-direction: column;
    align-items: center;
}
.title{
    width: 100%;
    text-align: center;
    color: grey;
    font-size: 32px;
    font-weight: 500;
    margin-bottom: 8px;
}
.desc{
    margin-top: 8px;
    color: grey;
    font-size: 24px;
    font-weight: 500;
}
.price{
    margin-top: 8px;
    color: blue;
    font-size: 24px;
    font-weight: 500;
}
.rate{
    color: grey;
    display: flex;
    gap: 8px;
}
</style>
