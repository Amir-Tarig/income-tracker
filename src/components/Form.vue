<template>
  <form  class="form" @submit.prevent="formHandler">
      <input type="text" id="desc" placeholder="Item to track.." v-model="formData.desc">
      <input type="number" id="num" placeholder="Value.." v-model="formData.value">
      <input type="date" id="date" v-model="formData.date">
      <input id="submit" type="submit" value="Submit">
  </form>
</template>

<script>
import { reactive } from 'vue'
export default {
    setup(props , {emit}) {
        const formData = reactive({
            desc: null,
            value:null,
            date: null
        })

        function formHandler(){
            emit("Handle-Data",{
                desc: formData.desc,
                value: formData.value,
                date: formData.date
            })

            formData.desc = null
            formData.value = null
            formData.date = null
        }

        return {
            formData,
            formHandler
        }
    }
}
</script>

<style scoped>
.form {
    /* border: 1px solid red; */
    width:70%;
    margin: auto;
    position: relative;
    display: flex;
    justify-content: space-around;
    top: 3em;
}

input {
    outline: none;
    width: 30%;
    border-radius: 10px;
    border-top-left-radius: 0;
    border-bottom-right-radius: 0;
    display: block;
    padding: .4em 1em;
    appearance: none;
    border: none;
    box-shadow: 1px 1px 1px rgba(0, 0, 0, 0.4), -1px -1px 1px rgba(0, 0, 0, 0.4);
}

#num{
    margin: 0  1em;
}

#submit {
    width: 15%;
    margin-left: 1em;
    outline: none;
}
</style>