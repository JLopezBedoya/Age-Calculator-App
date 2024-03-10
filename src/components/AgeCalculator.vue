<script setup>
import { ref } from 'vue';
    const day = ref(0)
    const month = ref(0)
    const year = ref(0)
    const time = ref({
        day: "29",
        month: "11",
        year: "86"
    })
    const Datehandle = ()=>{
        const current = new Date()
        time.value.year = current.getFullYear() - year.value
        time.value.month = current.getMonth() - (month.value-1)
        time.value.day = current.getDate() - day.value
    }
</script>

<template>
<div class="bg-purple-200 h-screen w-screen flex justify-center items-center">
    <section class="h-[60%] w-[90%] sm:w-[55%] sm:h-[70%] hz card p-5 grid grid-cols-1 grid-rows-6 bg-white font-bold">

        <article class="flex md:w-[80%] w-[100%]">
            <section>
                <p class="mb-1">DAY</p>
                <input v-model="day" class="p-2 text-lg md:text-2xl w-[75%] rounded-md border-purple-200 border-2" type="text" placeholder="DD">
            </section>
            <section>
                <p class="mb-1">MONTH</p>
                <input v-model="month" class="p-2 text-lg md:text-2xl w-[75%] rounded-md border-purple-200 border-2" type="text" placeholder="MM">
            </section>
            <section>
                <p class="mb-1">YEAR</p>
                <input v-model="year" class="p-2 text-lg md:text-2xl w-[75%] rounded-md border-purple-200 border-2" type="text" placeholder="YYYY">
            </section>
        </article>

        <article class="grid place-items-center relative w-[90%]">
            <button @click="Datehandle" class="absolute self-center md:right-0 bg-purple-600 hover:bg-purple-800 active:bg-purple-900 max-h-14 max-w-14 h-14 w-14 md:max-h-20 md:max-w-20 md:h-20 md:w-20 rounded-full text-white text-4xl md:text-5xl">&#10549;</button>
            <div class="border border-purple-100 border-t-2 w-[100%]"></div>
        </article>

        <article class="md:text-7xl text-5xl grid grid-rows-3 row-span-4">
            <p class="italian"><span class="italian text-purple-800">{{ time.year }}</span> years</p>
            <p class="italian"><span class="italian text-purple-800">{{ time.month }}</span> months</p>
            <p class="italian"><span class="italian text-purple-800">{{ time.day }}</span> days</p>
        </article>
    </section>
</div>
</template>

<style scoped>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,400;1,700&display=swap');
    *{
        font-family: "Poppins", sans-serif;
        font-weight: 400;
        font-style: normal;
    }
    .card{
        border-radius: 20px 20px 150px 20px;
    }
    .italian{
        font-family: "Poppins", sans-serif;
        font-weight: 700;
        font-style: italic;
    }
    @media screen and (min-width: 768px) and (max-width: 1023px) and (max-height: 500px){
        .hz{
            height: 100%;
        }
    }
</style>