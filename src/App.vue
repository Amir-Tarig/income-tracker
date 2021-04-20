<template>
  <Header :totalIncome="state.totalIncome"/>
  <Form  @Handle-Data="handleData"/>
</template>

<script>
import Header from './components/header.vue'
import Form from './components/Form.vue'
import {reactive , computed } from 'vue'
export default {
  name: 'App',
  components: {Header , Form},
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
           date: newD.getTime
         }]
      }
      return {
        handleData,
        state
      }
    }
}
</script>

<style>

</style>
