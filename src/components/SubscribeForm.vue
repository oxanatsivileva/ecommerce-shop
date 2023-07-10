<template>
    <form class="subscribe-form">
        <input 
            type="text" 
            placeholder="your@email.com" 
            class="input-text subscribe-form__input"
            :style="{backgroundColor: bgInput, color: colorText}"
        >
        <uiButton :color="colorButton || 'primary'">Sign up</uiButton>
    </form>

</template>

<script setup>
import uiButton from '@/components/UI/Button.vue'

const props = defineProps({
    bgInput: {
        type: String,
        required: false
    },
    colorButton: {
        type: String,
        required: false
    },
    colorText: {
        type: String,
        required: false
    }
})
</script>


<style lang="scss" scoped>
.subscribe-form {
    display: flex;
    &__input {
        flex-grow: 1;
    }
}
</style>