<template>
  <Header :totalIncome="state.totalIncome"/>
  <Form  @Handle-Data="handleData"/>
  <Income-list :state='state' />
</template>

<script>
import Header from './components/header.vue'
import Form from './components/Form.vue'
import {reactive , computed } from 'vue'
import IncomeList from './components/IncomeList.vue'
export default {
  name: 'App',
  components: {Header , Form, IncomeList},
    setup() {
      const state = reactive({
        income: [],
        totalIncome : computed(() => {
          let temp = 0;
          state.income.length > 0 ? state.income.map((el,i) => {
            temp += state.income[i].value
          }) : "";
          return temp;
        })
      })

      function handleData (data) {
        let d = data.date.split('-')
        let newD = new Date(d[0], d[1], d[2])

         state.income = [...state.income , {
           id: Date.now(),
           desc: data.desc,
           value: parseInt(data.value),
           date: newD.getTime()
         }]
         console.log(state.income)
      }
      return {
        handleData,
        state
      }
    }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #eee;
}
</style>
