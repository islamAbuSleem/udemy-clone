<template>
<div class=" pl-6 pr-2 mx-auto bg-white drop-shadow-lg">
    <div class=" flex align-center w-100 relative">
        <div class="py-5 font-bold text-gray-800 logo"><span class="cursor-pointer" @click="$router.push({name:'home'})"><img src="https://www.udemy.com/staticx/udemy/images/v7/logo-udemy.svg" alt="Udemy" class="w-21"></span></div>
        <div class="menu w-full flex">
            <ul class="menu-ul flex w-full items-center">
                <li class="py-6 px-3 text-gray-800 text-sm">
                    <span class="cursor-pointer hover:text-purple-700  transition duration-600 ease-in-out">Categories</span></li>
                <li class="py-2 px-3 text-gray-800 transition duration-600 ease-in-out rounded flex-grow">
                    <div class="search flex relative">
                        <input v-model="search" type="text" placeholder="Search for anything" class="bg-gray-50 border border-gray-800 w-full py-3 pl-12 outline-none rounded-full">
                        <button class="absolute left-4 top-3 h-1/2" ><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" :class="{'cursor-pointer':search,'cursor-not-allowed': !search}" :fill="!search ? 'Gray':'Neutral'" class="bi bi-search " viewBox="0 0 16 16">
                                <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z" />
                            </svg></button>
                    </div>
                </li>
                <li id="business" class=" py-6 px-3 text-gray-800 transition duration-600 ease-in-out text-sm"><span class="hover:text-purple-700 cursor-pointer" @mouseenter="udemyBusines = true" @mouseleave="udemyBusines = false">Udemy Business</span>
                    <div id="udemy-business" v-if="udemyBusines" class="w-1/5 bg-white font-bold text-base z-40 w-1/4 p-3 text-center shadow-md absolute right-1/3 -mr-8 top-20 delay-700 ">
                        <h2 class="mb-3">Get your team access to over 17,000 top Udemy courses, anytime, anywhere.
                        </h2>
                        <button class="bg-gray-900 block w-full text-white py-2 font-bold">Try Udemy
                            Business</button>
                    </div>
                </li>
                <li id="teach" class="py-6 px-3 text-gray-800  transition duration-600 ease-in-out text-sm">
                    <span class="hover:text-purple-700" @mouseenter="teachOnUdemy = true" @mouseleave="teachOnUdemy = false">Teach on Udemy</span>
                    <div v-if="teachOnUdemy" id="teach-udemy" class="bg bg-white font-bold text-base z-40 w-1/5 p-3 text-center top-20 right-1/4 -mr-10 shadow-md absolute delay-700  ">
                        <h2 class="mb-3">Turn what you know into an opportunity and reach millions around the world.</h2>
                        <button class="bg-gray-900 block w-full text-white py-2 font-bold">Learn More</button>
                    </div>
                </li>
                <li class="py-4 px-3 text-gray-800 transition duration-600 ease-in-out text-sm"><a href="#">
                        <div class="flex">
                            <span @click="$router.push({name:'cart'})" class="mx-1 py-2 pr-3 hover:text-purple-700 "><svg id="icon-cart" fill="udemy" viewBox="0 0 24 24" class="w-6 cursor-pointer" @mouseenter="cart = true" @mouseleave="cart = false">
                                    <path d="M15.55 13c.75 0 1.41-.41 1.75-1.03l3.58-6.49A.996.996 0 0020.01 4H5.21l-.94-2H1v2h2l3.6 7.59-1.35 2.44C4.52 15.37 5.48 17 7 17h12v-2H7l1.1-2h7.45zM6.16 6h12.15l-2.76 5H8.53L6.16 6zM7 18c-1.1 0-1.99.9-1.99 2S5.9 22 7 22s2-.9 2-2-.9-2-2-2zm10 0c-1.1 0-1.99.9-1.99 2s.89 2 1.99 2 2-.9 2-2-.9-2-2-2z">
                                    </path>
                                </svg>
                                <div v-if="cart" id="udemy-business" class="w-1/4 bg-white font-bold text-lg z-40 p-3 text-center shadow-md absolute right-1/4 top-20 -mr-24 delay-700  ">
                                    <span class="mb-3 text-md font-normal text-gray-500">Your cart is empty.</span>
                                    <span class=" text-purple-700 py-2 font-bold block text-sm">Keep shopping</span>
                                </div>
                            </span>
                            <button class=" mb-1 mx-1 bg-white border border-gray-700 py-2 px-5 shadow-md hover:bg-gray-50 transition duration-900 ease-in-out text-gray-700 font-bold" @click="$router.push({name:'login'})">Log in</button>
                            <button class=" mb-1 mx-1 bg-gray-900 py-2 px-4 shadow-md transition duration-900 ease-in-out text-white font-bold" @click="$router.push({name:'signup'})">Sign up</button>
                            <button class=" mb-1 mx-1 bg-white border border-gray-700 p-2 shadow-md hover:bg-gray-50 transition duration-900 ease-in-out text-gray-700 font-bold"><a href="/signup">
                                    <svg id="icon-language" viewBox="0 0 24 24" class="w-5">
                                        <path d="M11.99 2C6.47 2 2 6.48 2 12s4.47 10 9.99 10C17.52 22 22 17.52 22 12S17.52 2 11.99 2zm6.93 6h-2.95a15.65 15.65 0 00-1.38-3.56A8.03 8.03 0 0118.92 8zM12 4.04c.83 1.2 1.48 2.53 1.91 3.96h-3.82c.43-1.43 1.08-2.76 1.91-3.96zM4.26 14C4.1 13.36 4 12.69 4 12s.1-1.36.26-2h3.38c-.08.66-.14 1.32-.14 2s.06 1.34.14 2H4.26zm.82 2h2.95c.32 1.25.78 2.45 1.38 3.56A7.987 7.987 0 015.08 16zm2.95-8H5.08a7.987 7.987 0 014.33-3.56A15.65 15.65 0 008.03 8zM12 19.96c-.83-1.2-1.48-2.53-1.91-3.96h3.82c-.43 1.43-1.08 2.76-1.91 3.96zM14.34 14H9.66c-.09-.66-.16-1.32-.16-2s.07-1.35.16-2h4.68c.09.65.16 1.32.16 2s-.07 1.34-.16 2zm.25 5.56c.6-1.11 1.06-2.31 1.38-3.56h2.95a8.03 8.03 0 01-4.33 3.56zM16.36 14c.08-.66.14-1.32.14-2s-.06-1.34-.14-2h3.38c.16.64.26 1.31.26 2s-.1 1.36-.26 2h-3.38z">
                                        </path>
                                    </svg>

                                </a></button>
                        </div>
                    </a></li>x
            </ul>
        </div>
    </div>

</div>
</template>

<script lang="ts" setup>
import {ref} from 'vue';

let search:string = ref('');
let udemyBusines:boolean = ref(false);
let teachOnUdemy:boolean = ref(false);
let cart:boolean = ref(false);

</script>

<style lang="scss" scoped>
.logo {
    width: 100px;
}
</style>
