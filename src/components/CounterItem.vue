<template>
  <div class="item">
    <h4>{{ category.title }}</h4>
    <div class="changes">
      <span class="val">{{ category.counter }}</span>

      <button class="changeVal" type="button" @click="decrement">-</button>
      <button class="changeVal" type="button" @click="increment">+</button>
      <button class="deleteCat" @click="removeCategory">
        Delete this category
      </button>
    </div>
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