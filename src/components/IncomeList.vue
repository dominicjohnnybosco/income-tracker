<template>
    <div class="income-list">
        <!-- <IncomeItem v-for="data in income" :key="data.id" :income="data" />
        <h1>{{ incomeArray }}</h1>
        <IncomeItem :test="incomeArray" /> -->
        <!-- <IncomeItem :test="state" /> -->
    </div>
</template>

<script>
// import { reactive, computed, toRefs} from 'vue'
// import IncomeItem from './IncomeItem'
    export default {
        name: 'IncomeList',
        components: {
            // IncomeItem,
        },
        // setup (){
        //     const state = reactive({
        //         income: ['hello', 'world']
        //     })
        //     const incomeArray = computed(() => {
        //         let first = state.income[0]
        //         let second = state.income[1]
        //         return first + " " + second
        //     } ) 

        //     return {
        //         ...toRefs(state),
        //         incomeArray,
        //     } 
        // } 
    }  
</script>

<style scoped>
    .income-list {
        margin-top: 30px;
        padding: 15px;
    } 

</style>