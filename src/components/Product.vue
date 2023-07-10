<template>
    <div class="product">
        <router-link :to="`products/${id}`">
            <img :src="img" :alt="title" class="product-image">
        </router-link>
        <router-link :to="`products/${id}`" class="product-name">{{title}}</router-link>
        <span class="product-name__price">£ {{price}}</span>

    </div>
</template>

<script setup>
const props = defineProps({
    id: {
        type: String,
        required: true
    },
    img: {
        type: String,
        required: true
    },
    title: {
        type: String,
        required: true
    },
    price: {
        type: Number,
        required: true
    }

})
</script>

<style lang="scss" scoped>
.product {
    &-image {
        display: block;
        width: 100%;
        margin-bottom: 24px;
        object-fit: cover;
    }
    &-name {
        display: block;
        font-family: var(--clash);
        font-size: 20px;
        line-height: 140%;
        color: var(--dark-primary);
        margin-bottom: 8px;
        text-decoration: none;
        &:hover {
            text-decoration: underline;
        }
        @media screen and (max-width: 767px) {
            font-size: 16px;
        }
        &__price {
            display: block;
            font-size: 18px;
            line-height: 150%;
            color: var(--dark-primary);
            @media screen and (max-width: 767px) {
                font-size: 15px;
            }

        }
    }
}
</style>