<script setup>
import { ref } from 'vue';

    const time = ref({
        day: "--",
        month: "--",
        year: "--"
    })
</script>

<template>
<div class="bg-purple-200 h-screen w-screen flex justify-center items-center">
    <section class="md:w-[50%] md:h-[75%] card p-5 grid grid-cols-1 grid-rows-6 bg-white font-bold">

        <article class="flex justify-between w-[80%]">
            <section>
                <p class="mb-1">DAY</p>
                <input class="p-2 text-2xl w-[70%] rounded-md border-purple-200 border-2" type="text" placeholder="DD">
            </section>
            <section>
                <p class="mb-1">MONTH</p>
                <input class="p-2 text-2xl w-[70%] rounded-md border-purple-200 border-2" type="text" placeholder="MM">
            </section>
            <section>
                <p class="mb-1">YEAR</p>
                <input class="p-2 text-2xl w-[70%] rounded-md border-purple-200 border-2" type="text" placeholder="YYYY">
            </section>
        </article>

        <article class="grid place-items-center relative w-[90%]">
            <button class="absolute right-0 bg-purple-600 hover:bg-purple-800 active:bg-purple-900 max-h-20 max-w-20 h-20 w-20 rounded-full text-white text-6xl">&#10549;</button>
            <div class="border border-purple-100 border-t-2 w-[100%]"></div>
        </article>

        <article class="text-7xl grid grid-rows-3 row-span-4">
            <p class="italian"><span class="text-purple-600">{{ time.year }}</span> Years</p>
            <p class="italian"><span class="text-purple-600">{{ time.month }}</span> months</p>
            <p class="italian"><span class="text-purple-600">{{ time.day }}</span> days</p>
        </article>
    </section>
</div>
</template>

<style scoped>
    @import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,500;1,500&display=swap');
    *{
        font-family: "Montserrat", sans-serif;
        font-style: normal;
    }
    .card{
        border-radius: 20px 20px 200px 20px;
    }
    .italian{
        font-family: "Montserrat", sans-serif;
        font-style: normal;
        font-style: italic;
    }
</style>