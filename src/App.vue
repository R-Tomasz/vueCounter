<template>
  <div>
    <h1>Counter</h1>
    <CounterApp />
  </div>
</template>

<script>
import CounterApp from "./components/CounterApp.vue";

export default {
  components: {
    CounterApp,
  },
};
</script>

<style scoped>
.item {
  border: 1px solid black;
}
</style>