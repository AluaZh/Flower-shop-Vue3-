<script setup>
defineProps({
    title: String,
    composition: String,
    imageUrl: String,
    price: Number,
    isFavorite: Boolean,
    isAdded: Boolean,
    onClickAdd: Function,
    onClickFavorite: Function
})

</script>

<template>
    <div class="relative bg-white border-slate-100 rounded-3xl p-8 cursor-pointer transition hover:-translate-y-2 hover:shadow-xl">
        <img @click="onClickFavorite" :src="!isFavorite ? '/like-1.png' : '/like-2.png'" alt="Like" class="absolute top-0 left-7" />
        <img :src="imageUrl" alt="" class="w-40 rounded-xl" />

        <p class="mt-2 font-bold">{{ title.slice(7, -1) }}</p>
        <p class="text-slate-400 text-xs mt-2">{{ composition }}</p>

        <div class="flex justify-between mt-3 items-center">
            <div class="flex flex-col">
                <span class="text-slate-400">Cost:</span>
                <b>{{ price }} tg</b>
            </div>
            <img @click="onClickAdd" :src="!isAdded ? '/add.png' : '/added.png'" alt="" class="w-5 h-5">
        </div>
    </div>
</template>