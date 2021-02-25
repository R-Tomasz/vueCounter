<template>
  <div class="item">
    <h4>{{ category.title }}</h4>
    <p>{{ category.counter }}</p>
    <button type="button" @click="decrement">-</button>
    <button type="button" @click="increment">+</button>
    <button @click="removeCategory">Delete this category</button>
  </div>
</template>

<script>
export default {
  props: ["category"],
  methods: {
    increment() {
      this.$emit("incrementClicked", this.category.id);
    },
    decrement() {
      this.$emit("decrementClicked", this.category.id);
    },
    removeCategory() {
      this.$emit("removeClicked", this.category.id);
    },
  },
};
</script>