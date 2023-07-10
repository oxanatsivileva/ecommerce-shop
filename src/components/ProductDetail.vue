<template>
    <div class="product">
        <div>
            <img :src="product.image" :alt="product.name">
        </div>
        <div>
            <h2 class="product-name">{{ product.name }}</h2>
            <span class="product-price">£{{ product.price }}</span>
            <div class="product-block product-description">
                <span class="product-block__title">Product description</span>
                <div v-html="product.description"></div>
            </div>
            <div class="product-block">
                <span class="product-block__title">Dimensions</span>
                <span 
                    class="product-param" 
                    v-for="(param, i) of product.params"
                    :key="i"
                >
                    {{ param.title }}: {{ param.value }}
                </span>
            </div>
            <div class="product-block">
                <span class="product-block__title">Quantity</span>
                <div class="product-quantity">
                    <span class="product-quantity-symbol" @click="changeQuantity('minus')">-</span>
                    <span class="product-quantity-value">{{quantity}}</span>
                    <span class="product-quantity-symbol" @click="changeQuantity('plus')">+</span>

                </div>
            </div>
            <Button @click="cartStore.addToCart(product, quantity)">Add to cart</Button>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import Button from '@/components/UI/Button.vue'
import {useCartStore} from '@/store/cart.js'

const props = defineProps({
    product: {
        type: Object,
        default: () => {},
        required: true
    }
})

const quantity = ref(1);
const cartStore = useCartStore()

const changeQuantity = (type) => {
    if (type === 'minus') {
        quantity.value === 1 ? (quantity.value = 1) : quantity.value--
    }
    if (type === 'plus') {
        quantity.value === 3 ? (quantity.value = 3) : quantity.value++
    }
}
    
</script>

<style lang="scss" scoped>
.product {
    background: var(--lightgray);
    padding: 50px 80px;
    display: grid;
    grid-template-columns: 1fr 500px;
    column-gap: 65px;
    margin-bottom: 65px;
    align-items: center;
    color: var(--dark-primary);

    &-name {
        margin-bottom: 16px;
        font-family: var(--clash);
        font-size: 36px;
        line-height: 44px;
        color: var(--dark-primary);
    }
    &-price {
        display: block;
        font-size: 24px;
        line-height: 32px;
        margin-bottom: 28px;
        color: var(--dark-primary);
    }
    &-block {
        margin-bottom: 40px;
        &__title {
            display: block;
            margin-bottom: 14px;
            line-height: 20px;
            font-family: var(--clash);
        }
    }
    &-description {
        border-top: 1px solid var(--border-grey);
        padding-top: 24px;
    }
    &-param {
        display: block;
    }
    &-quantity {
        width: 122px;
        height: 46px;
        background: #FFFFFF;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 16px;
        &-symbol {
            color: var(--border-grey);
            cursor: pointer;
        }
    }

    
}
</style>