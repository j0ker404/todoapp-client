<template>
  <div id="app">
    <Heading title="To Do" />
    <AddItem v-on:newItem="foo" />
    <ListContent v-bind:data="data" />
  </div>
</template>

<script>
import Heading from "./components/Header";
import ListContent from "./components/ListContent";
import AddItem from "./components/AddItem";

export default {
  name: "App",
  components: {
    Heading,
    ListContent,
    AddItem,
  },
  data: () => {
    return {
      data: [
        { id: 0, title: "Do task 1", status: true },
        { id: 1, title: "Do task 2", status: false },
        {
          id: 2,
          title:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Nemo architecto expedita, deserunt quidem fuga eveniet rem doloremque, molestiae facere iste pariatur! Velit, iste autem eligendi rem recusandae consectetur. Soluta, magnam.Quae voluptatem veritatis incidunt magnam provident cum quos doloremque id suscipit quidem earum recusandae, quam delectus aliquam officia ipsa nisi harum nam iure impedit asperiores amet inventore optio aut? Consequatur.",
          status: false,
        },
      ],
    };
  },
  methods: {
    foo: function(text) {
      console.log(`Received ${text}`);
    },
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
