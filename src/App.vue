<template>
  <div id="app">
    <Heading title="To Do" />
    <AddItem v-on:newItem="addNewItem" />
    <ListContent
      v-bind:data="data"
      v-on:removeMe="removeItem"
      v-on:status="updateStatus"
    />
  </div>
</template>

<script>
import Heading from "./components/Header";
import ListContent from "./components/ListContent";
import AddItem from "./components/AddItem";
import axios from "axios";

export default {
  name: "App",
  components: {
    Heading,
    ListContent,
    AddItem,
  },
  data: () => {
    return {
      data: [],
    };
  },
  methods: {
    addNewItem: function(text) {
      // add new item into database
      axios
        .post("http://localhost:3000/add", { title: text })
        .then((res) => {
          // console.log("Vue method called");
          console.log(res.data);
        })
        .catch((err) => console.log(err));
      // update data field
      this.data = [];
      this.setData();
    },
    setData: function() {
      // updates data to values in backend
      axios
        .get("http://localhost:3000/getList")
        .then((res) => {
          this.data = res.data;
          // console.log("Vue method called");
          // console.log(res.data);
        })
        .catch((err) => console.log(err));
    },
    removeItem: function(itemID) {
      // call back function for "removeMe" event
      // remove item
      axios
        .delete("http://localhost:3000/delete", {
          data: { id: itemID },
        })
        .catch((err) => console.log(err));
      // update data
      this.setData();
    },
    updateStatus: function(itemData) {
      // console.log("boom");
      axios
        .put("http://localhost:3000/update", {
          id: itemData.id,
        })
        .catch((err) => console.log(err));
      // update data
      this.setData();
    },
  },
  created: function() {
    // update data field on creation of component
    this.setData();
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
