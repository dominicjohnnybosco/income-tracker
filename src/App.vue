<template>
  <HeaderCom :totalIncome="totalIncome" />
  <FormCom @add-income="AddIncome" />
  <IncomeList :state="state" />
  <!-- <h2 v-for="data in income" :key="data.id">hello {{data.value}}</h2> -->
  <div class="income-list">
      <div class="income-item" v-for="data in income" :key="data.id">
          <div class="removeItem">X</div>
          <div class="desc">{{ data.desc || 'No Description' }}</div>
          <div class="price">{{ data.value ? `$${data.value}` : '$0' }}</div>
          <div class="date">{{ data.date || 'No Date' }}</div>
      </div>
  </div>

</template>

<script>
import { reactive, computed, toRefs } from 'vue'
import FormCom from './components/FormCom.vue'
import HeaderCom from './components/HeaderCom.vue'
import IncomeList from './components/IncomeList.vue'

export default {
  name: 'App',
   components: {
    HeaderCom,
    FormCom,
    IncomeList,
  },
  setup() {
    const state = reactive({
      income: [],
      totalIncome: computed(() => {
        let temp = 0

        if (state.income.length > 0) {
          for (let i = 0; i < state.income.length; i++) {
            temp += state.income[i].value
          } 
        } 
        return temp
      }),
      
    })
      

    function AddIncome(data) {
      let d = data.date.split("-")
      let newD = new Date(d[0], d[1], d[2])

      state.income = [...state.income, {
        id: Date.now(),
        desc: data.desc,
        value: data.value,
        date: newD.getTime()
      }] 
      // console.log(state.income.date)
    }
     let formatedDate = computed((state) => {
        let date = new Date(state.income.date);
        let day = date.getDate();
        let month = date.getMonth();
        let year = date.getFullYear();

        let newDate = day + "/" + month + "/" + year;
        return newDate
     }) 

    return {
      ...toRefs(state),
      AddIncome,
      formatedDate,
    } 
  },

}  
</script>

<style >
  * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Fira Sans', sans-serif;
  } 

  body {
    background: #EEE;
  }

   .income-list {
        margin-top: 30px;
        padding: 15px;
    } 

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
