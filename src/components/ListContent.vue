<template>
  <div id="lsContent">
    <!-- <ListItem v-bind:itemData="data[2]"/> -->
    <div v-for="item in data" v-bind:key="item.id">
      <ListItem
        v-bind:itemData="item"
        v-on:removeMe="remove"
        v-on:updateStatus="status"
      />
    </div>
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";
export default {
  name: "ListContent",
  components: {
    ListItem,
  },
  props: ["data"],
  methods: {
    remove: function(id) {
      // call back function that sends request to be removed to 'Appl
      // console.log(`Remove me please: ${id}`);
      this.$emit("removeMe", id);
      // console.log("remove");
    },
    status: function(itemData) {
      // call back function that sends request to be updateStatus to "ListContent"
      // console.log("boom");
      this.$emit("status", {
        id: itemData.id,
      });
    },
  },
};
</script>

<style scoped></style>
