<script setup>
import { ref } from 'vue';
    const day = ref(17)
    const month = ref(4)
    const year = ref(2007)
    const day31 = [0, 2, 4, 6, 7, 9, 11]
    const day30 = [3, 5, 8, 10]
    const error = [false,false,false]
    const time = ref({
        day: "--",
        month: "--",
        year: "--"
    })
    const Datehandle = ()=>{
        const current = new Date()
        var condition = true
        if(day31.includes(month.value-1)){
            condition = day.value < 32 && day.value > 0
        }else if(day30.includes(month.value-1)){
            condition = day.value < 31 && day.value > 0
        }else if(month.value-1 == 1){
            condition = day.value < 30 && day.value > 0
        }else{
            condition = false
        }
        if(condition && month.value >= 0 && month.value <=12 && current.getFullYear() >= year.value){
            let monthCondition = current.getMonth() - (month.value-1)
            let dayCondition = current.getDate() - day.value
            console.log(dayCondition);
            let getDay = (dayCondition > 0 ? dayCondition: 30-Math.abs(dayCondition))
            let getMonth = (monthCondition > 0 ? monthCondition: 12-Math.abs(monthCondition))
            let getYear = (current.getFullYear() - year.value)-(monthCondition > 0 ? 0:(monthCondition == 0) ? dayCondition >= 0 ? 0:1:1)
            time.value = {
                year: getYear,
                month: (getMonth == 12 ? 0:getMonth),
                day: (getDay == 30 ? 0:getDay)
            }
        }else{
            time.value = {
                day: "--",
                month: "--",
                year: "--"
            }
        }
        if (!condition) {
                error[0] = true
            }else{
                error[0] = false
            }
            if (month.value < 0 || month.value > 12) {
                error[1] = true
            }else{
                error[1] = false
            }
            if (current.getFullYear() < year.value) {
                error[2] = true
            }else{
                error[2] = false
            }
    }
</script>

<template>
<div class="bg-purple-200 h-screen w-screen flex justify-center items-center">
    <section class="h-[60%] w-[90%] sm:w-[55%] sm:h-[70%] hz card p-5 grid grid-cols-1 grid-rows-7 bg-white font-bold">

        <article class="flex md:w-[80%] w-[100%] row-span-2">
            <section>
                <p :class="`mb-1 ${error[0] ? 'text-red-500':''}`">DAY</p>
                <input v-model="day" :class="`p-2 text-lg md:text-2xl w-[75%] rounded-md border-purple-200 border-2 ${error[0] ? 'text-red-500 border-red-500':''}`" type="text" placeholder="DD">
                <p v-if="error[0]" class="text-red-500 text-xs">Must be a valid day</p>
            </section>
            <section>
                <p :class="`mb-1 ${error[1] ? 'text-red-500':''}`">MONTH</p>
                <input v-model="month" :class="`p-2 text-lg md:text-2xl w-[75%] rounded-md border-purple-200 border-2 ${error[1] ? 'text-red-500 border-red-500':''}`" type="text" placeholder="MM">
                <p v-if="error[1]" class="text-red-500 text-xs">Must be a valid month</p>
            </section>
            <section>
                <p :class="`mb-1 ${error[2] ? 'text-red-500':''}`">YEAR</p>
                <input v-model="year" :class="`p-2 text-lg md:text-2xl w-[75%] rounded-md border-purple-200 border-2 ${error[2] ? 'text-red-500 border-red-500':''}`" type="text" placeholder="YYYY">
                <p v-if="error[2]" class="text-red-500 text-xs">Must be a valid Year</p>
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
    @media screen and (min-width: 760px) and (max-width: 1023px) and (max-height: 500px){
        .hz{
            height: 100%;
        }
    }
</style>