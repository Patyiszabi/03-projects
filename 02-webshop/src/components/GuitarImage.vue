<script setup>
defineProps({
    title: {
        type: String,
        required: true
    }
})
</script>

<template>
    <img :src="`guitars/${title}.jpg`" :alt="title" class="guitar-image" />
</template>


<style scoped>
.guitar-image {
    width: 15%;
    display: block;
    margin: 0 auto;
    text-align: center;
    height: auto;
    border-radius: 8px;
}
</style>

