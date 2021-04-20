<template>
 <div class="income-list">
      <Items v-for="data in state.income" :key="data.id" :income="data"/>
 </div>
</template>

<script>
import Items from './Items.vue'
export default {
    components: {Items},
    props: {
        state: Object
    }
}
</script>

<style scoped>
    .income-list {
        margin-top: 60px;
        padding: 15px;
    }
</style>