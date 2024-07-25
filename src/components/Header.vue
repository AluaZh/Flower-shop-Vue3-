<template>
    <header class="flex justify-between border-b border-slate-200 px-10 py-5">
        
        <div class="flex items-center gap-4">
            <img src="/logo.png" alt="Logo" class="w-10"/>
            <div>
                <h2 class="text-xl font-bold uppercase">Vue Flowers</h2>
                <p class="text-slate-400">Flower for you</p>
            </div>
        </div>

        <ul class="flex items-center gap-10">
            <li class="flex items-center cursor-pointer gap-3 text-slate-500 hover:text-black">
                <img src="/card.png" alt="" class="w-5"/>
                <b>10.000 tg</b>
            </li>

            <li class="flex items-center cursor-pointer gap-3 text-slate-500 hover:text-black">
                <img src="/fav.png" alt="" class="w-5"/>
                <span>Favorite</span>
            </li>

            <li class="flex items-center cursor-pointer gap-3 text-slate-500 hover:text-black">
                <img src="/profile.png" alt="" class="w-5"/>
                <span>Profile</span>
            </li>
        </ul>

    </header>
</template>