<template>
    <div class="income-item">
        <!-- <div class="removeItem">X</div>
        <div class="desc">{{ income.desc || 'No Description' }}</div>
        <div class="price">{{ income.value ? `$${income.value}` : '$0' }}</div>
        <div class="date">{{ income.date || 'No Date' }}</div> -->
       <!-- <h1>{{ test }}</h1> -->
    </div>
</template>

<script>
    export default {
        name: 'IncomeItem',
        props: {
            income:{
                type: Object
            },
            // test: Object 
        } 
         
    }
</script>

<style scoped>
    .income-item {
        position: relative;
        display:flex;
        padding: 15px 15px 15px 0px;
        background-color: #fff;
        border-radius: 8px;
        max-width: 600px;
        margin: 0 auto 30px;
    }     

    .removeItem {
        color: #ef2020;
        font-weight: 600;
        font-size: 20px;
        line-height: 1;
        text-align: center;
        margin: 0 15px;

    }
    
    .desc {
        color: #666;
        flex: 1 1 100%;
        font-size: 20px;
    }

    .price {
        color:#666;
        min-width: 100px;
        font-size: 20px;
    }

    .date {
        color:#666;
        text-align: right;
        font-size: 20px;
    } 

</style>