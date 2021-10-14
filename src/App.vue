<template>
    <div class="app">
        <header>
            <div class="title">
                <img src="./assets/gravity-falls-waddles.png" alt="Gravity falls waddles" />
                <h1>Gravity Falls Jobs</h1>
            </div>
            <div class="order">
                <button @click="handleClick('title')">Order by title</button>
                <button @click="handleClick('salary')">Order by salary</button>
                <button @click="handleClick('location')">Order by location</button>
            </div>
        </header>
        <job-list :jobs="jobs" :order="order" />
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

import Job from './types/Job'
import OrderTerm from './types/OrderTerm'

import JobList from './components/JobList.vue'

export default defineComponent({
    name: 'App',
    components: { JobList },
    setup() {
        const jobs = ref<Job[]>([
            { title: 'Explorer', location: 'City', salary: 50, id: '1' },
            { title: 'Investigator', location: 'Gravity Falls woods', salary: 80, id: '2' },
            { title: 'Waiter', location: 'Diner', salary: 40, id: '3' },
            { title: 'Cashier', location: 'Mistery Shack', salary: 10, id: '4' },
            { title: 'Janitor', location: 'Whereabouts', salary: 20, id: '5' }
        ])
        const order = ref<OrderTerm>('title')

        const handleClick = (term: OrderTerm) => {
            order.value = term
        }

        return { jobs, handleClick, order }
    }
})
</script>

<style>
header {
    text-align: center;
}
header .order {
    margin-top: 20px;
}
button {
    margin: 0 10px;
    color: #1b6e8f;
    border: 3px solid #11c98c;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
}
header .title {
    display: flex;
    justify-content: center;
}
header img {
    width: 150px;
    margin-right: 30px;
}
header h1 {
    font-size: 3em;
}
</style>
