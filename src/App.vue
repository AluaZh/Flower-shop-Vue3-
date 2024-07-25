<script setup>
import { onMounted, ref, reactive, watch } from 'vue';
import axios from 'axios';

import Header from './components/Header.vue';
import CardList from './components/CardList.vue';
import Drawer from './components/Drawer.vue';

const items = ref([]);
const filters = reactive({
  sortBy: 'composition',
  searchQuery: ''
})

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value;
}

const onChangeSearchInput = (event) => {
  filters.searchQuery = event.target.value
  console.log(filters.searchQuery)
}


const fetchFavorites = async () => {
  try {
    const {data: favorites} = await axios.get('https://6b8c42cc3891e85c.mokky.dev/favorite')

    items.value = items.value.map((item) => {
      const favorite = favorites.find(favorite => favorite.parentId === item.id);

      if(!favorite) {
        return item;
      }

      return {
        ...item,
        isFavorite: true,
        favoriteId: favorite.id,
      }
    })
  } catch(err) {
    console.log(err)
  }
} 



const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy
    }

    if(filters.searchQuery) {
      params.composition = `*${filters.searchQuery}*`;
    }

    const {data} = await axios.get(
      `https://6b8c42cc3891e85c.mokky.dev/items`,
      {
        params
      }
    );
    items.value = data.map((obj) => ({
      ...obj,
      isFavorite: false,
      isAdded: false
    }))
  } catch (err) {
    console.log(err)
  }
}

onMounted(async () => {
  await fetchItems();
  await fetchFavorites();
});
watch(filters, fetchItems)
</script>

<template>
  <div class="bg-white w-4/5 m-auto h-full rounded-xl shadow-xl mt-8 mb-8">
    <!-- <Drawer /> -->
    <Header />

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-5">Gallery</h2>
        
        <div class="flex gap-4">
          <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none">
            <option value="name">By names</option>
            <option value="price">By price(cheep)</option>
            <option value="-price">By price(expensive)</option>
          </select>

          <div class="relative">
            <img src="/search.png" alt="" class="w-5 absolute left-4 top-3 opacity-50">
            <input @input="onChangeSearchInput" type="text" placeholder="Search..." class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400">
          </div>
        </div>
      </div>

      <div class="mt-10">
        <CardList :items="items" />
      </div>
    </div>
  </div>
</template>

<style>

</style>
