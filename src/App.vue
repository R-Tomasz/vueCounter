<template>
  <div id="main-container">
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