<template>
    <div 
        class="hero-info"
        :style="{backgroundColor: background}" 
        :class="{'hero-info--mobile-padding' : mobilePadding }">
        <div class="hero-info__container">
            <div 
                class="hero-info__text"
                >
                <h2 
                    class="hero-info__title"
                    :style="{color: colorTitle}">{{title}}</h2>
                <span 
                    class="hero-info__descr"
                    :style="{color: colorDescription}">{{description}}</span>
            </div>
        </div>
        <uiButton :mobileFullWidth="true" :color="colorLink || 'secondary'" type="link" to="/">
            View collection
        </uiButton>

    </div>
</template>

<script setup>
import uiButton from '@/components/UI/Button.vue'

const props = defineProps({
    title: {
        type: String,
        required: false
    },
    description: {
        type: String,
        required: false
    },
    link: {
        type: String,
        required: false
    },
    colorTitle: {
        type: String,
        default: ''
    },
    colorDescription: {
        type: String,
        default: '#5B5676'
    },
    colorLink: {
        type: String,
        required: false
    },
    background: {
        type: String,
        default: '#fff'
    },
    mobilePadding: {
        type: Boolean,
        default: false
    }
})

</script>

<style lang="scss" scoped>
.hero {
    &-info {
        background: #fff;
        max-width: 630px;
        padding: 50px 55px;
        min-height: 444px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: flex-start;

        @media screen and (max-width: 767px) {
            padding: 47px 0px 0px;
            min-height: 0;
            max-width: 100%;        
        }

        &__container {
            @media screen and (max-width: 767px) {
                padding: 0;
            } 
        }

        &__text {
            @media screen and (max-width: 767px) {
                margin-bottom: 32px;
            }
        }

        &__title {
            font-family: var(--clash);
            font-size: 32px;
            line-height: 140%;
            margin-bottom: 20px;
            @media screen and (max-width: 767px) {
                font-size: 24px;            
            }
        }
        &__descr {
            font-size: 18px;
            line-height: 150%;
            color: #5B5676;        
        }
        &--mobile-padding {
            @media screen and (max-width: 767px) {
                padding: 36px 32px;            
            }
        }
    }
}
</style>