<template>
    <div class="products-container">
        <div class="products">
            <Product
                v-for="product of products"
                :id="product.id"
                :key="product.id"
                :img="product.img"
                :title="product.title"
                :price="product.price"
            />
        </div>
        <div class="products-link">
          <uiButton 
            :mobileFullWidth="true" 
            color="lightgray" 
            type="link" 
            to="/" 
          >
            View collection
          </uiButton>
        </div>
    </div>

</template>

<script setup>
import {ref} from 'vue'
import Product from '@/components/Product.vue'
import uiButton from '@/components/UI/Button.vue'

const props = defineProps ({
  products: {
    required: true
  }
})


// const products = ref([
//   {
//     id: 1,
//     img: '/img/product1.jpg',
//     title: 'The Dandy chair',
//     price: 250
//   },
//   {
//     id: 2,
//     img: '/img/product2.jpg',
//     title: 'Rustic Vase Set',
//     price: 155
//   },
//   {
//     id: 3,
//     img: '/img/product3.jpg',
//     title: 'The Silky Vase',
//     price: 125
//   },
//   {
//     id: 4,
//     img: '/img/product4.jpg',
//     title: 'The Lucy Lamp',
//     price: 399
//   }
// ])
</script>

<style lang="scss" scoped>
.products {
    padding: 0 80px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    column-gap: 20px;
    margin-bottom: 64px;
    @media screen and (max-width: 1024px) {
      grid-template-columns: repeat(2, 1fr);
      row-gap: 20px;
    }
    @media screen and (max-width: 767px) {
      padding: 0;
    }
    &-container {
      margin-bottom: 56px;
    }
    &-link {
      text-align: center;
    }
}
</style>