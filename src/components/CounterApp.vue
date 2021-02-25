<template>
  <div id="app">
    <input type="text" placeholder="Kategoria" v-model="newItem" />
    <button @click="addCategory">Add category</button>
    <CounterItem
      :category="category"
      v-for="category in categories"
      v-bind:key="category.id"
      @incrementClicked="increment"
      @decrementClicked="decrement"
      @removeClicked="removeCategory"
    />
  </div>
</template>

<script>
import CounterItem from "./CounterItem";

export default {
  components: {
    CounterItem,
  },
  data() {
    return {
      newItem: "",
      categories: [
        { title: "Kawy", counter: 0, id: 0 },
        { title: "Przeczytane strony", counter: 0, id: 1 },
      ],
    };
  },
  methods: {
    getId() {
      let idPosition = 0;
      for (var i = 0; i < this.categories.length; i++) idPosition++;
      return idPosition;
    },
    addCategory() {
      if (this.newItem != "") {
        this.categories.push({
          title: this.newItem,
          counter: 0,
          id: this.getId() + 1,
        });
      }
      this.newItem = "";
    },
    removeCategory(id) {
      var index = this.categories.findIndex((el) => el.id === id);
      this.categories.splice[(this.categories[index], 1)];
    },
    increment(id) {
      var index = this.categories.findIndex((el) => el.id === id);
      this.categories[index].counter += 1;
    },
    decrement(id) {
      var index = this.categories.findIndex((el) => el.id === id);
      if (this.categories[index].counter > 0)
        this.categories[index].counter -= 1;
    },
  },
};
</script>

<style>
</style>
