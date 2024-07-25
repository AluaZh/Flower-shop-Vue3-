<script setup>
import DrawerHead from './DrawerHead.vue';
import CartItemList from './CartItemList.vue';
</script>

<template>
    <div>
        <div class="fixed top-0 left-0 h-full w-full z-10 bg-black opacity-70"></div>
        <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
            <DrawerHead />
            <CartItemList />

            <div class="flex flex-col gap-4 mt-7">
                <div class="flex gap-2">
                    <span>Itogo:</span>
                    <div class="flex-1 border-b border-dashed"></div>
                    <b>20000 tg</b>
                </div>

                <div class="flex gap-2">
                    <span>Nalig:</span>
                    <div class="flex-1 border-b border-dashed"></div>
                    <b>5%</b>
                </div>

                <button 
                    disabled=""
                    class="mt-4 transition bg-lime-500 w-full rounded-xl py-3 text-white disabled:bg-slate-300 hover:bg-lime-600 active:bg-lime-700 cursor-pionter"
                >Order a zakaz</button>
            </div>
        </div>
    </div>
</template>