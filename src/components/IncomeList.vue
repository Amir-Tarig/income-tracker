<template>
 <div class="income-list">
      <Items @remove-item="removeItem" v-for="data in state.sortedIncome" :key="data.id" :income="data"/>
 </div>
</template>

<script>
import Items from './Items.vue'
export default {
    components: {Items},
    props: {
        state: Object
    },
    setup(props,{emit}) {
        function removeItem(id){
            emit("remove-Item", id)
        }

        return {
            removeItem
        }
    }
}
</script>

<style scoped>
    .income-list {
        margin-top: 60px;
        padding: 15px;
    }
</style>