<template>
  <div id="app">
    <input type="text" placeholder="Category" v-model="newItem" />
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
      categories: [],
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
      this.categories.splice(index, 1);
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
#main-container {
  min-width: 50%;
  padding: 3rem 0;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
  border: 1px solid black;
  display: inline-block;
  -webkit-box-shadow: 10px 10px 20px -11px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 10px 10px 20px -11px rgba(0, 0, 0, 0.75);
  box-shadow: 10px 10px 20px -11px rgba(0, 0, 0, 0.75);
}

.val {
  padding: 0 10px;
}

.changes {
  display: inline-block;
}
.item {
  background-color: #fafafa;
}

.deleteCat {
  display: block;
  margin-bottom: 15px;
  margin-top: 15px;
}
.changeVal {
  display: inline-block;
}
</style>
