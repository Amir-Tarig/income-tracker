<template>
  <header class="header">
      <h1 class="logo">Income Tracker</h1>
      <h2 class="total-income">${{ totalIncome }}</h2>
  </header>
</template>

<script>
export default {
    props: {
        totalIncome: Number
    }
}
</script>

<style scoped>
.header {
    background: #606c38;
    color: #f1faee;
    display: flex;
    justify-content: space-around;
    padding: 1em 0;
}

.total-income{
    background: #606c38;
    padding: 10px 2em;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, .2), -1px -1px 10px rgba(0, 0, 0, .2);
}

.logo{
    font-style: italic ;
}
</style>

