<script setup>
import Card from './Card.vue';

defineProps({
    items: Array
})


const onClickAdd = () => {
    alert("Add!")
}
</script>

<template>
    <div class="grid grid-cols-4 gap-5">
        <Card 
            v-for="item in items"
            :key="item.id"
            :title="item.title" 
            :composition="item.composition"
            :imageUrl="item.imgURL" 
            :price="item.price"
            :on-click-add="onClickAdd"
            :is-favorite="item.isFavorite"
        />
    </div>
</template>