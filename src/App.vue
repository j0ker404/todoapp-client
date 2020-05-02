/* eslint-disable */
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
      datas: [
        { id: 0, title: "Do task 1", status: true },
        { id: 1, title: "Do task 2", status: false },
        {
          id: 2,
          title:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Nemo architecto expedita, deserunt quidem fuga eveniet rem doloremque, molestiae facere iste pariatur! Velit, iste autem eligendi rem recusandae consectetur. Soluta, magnam.Quae voluptatem veritatis incidunt magnam provident cum quos doloremque id suscipit quidem earum recusandae, quam delectus aliquam officia ipsa nisi harum nam iure impedit asperiores amet inventore optio aut? Consequatur.",
          status: false,
        },
      ],
      data: [],
    };
  },
  methods: {
    foo: function(text) {
      console.log(`Received ${text}`);
    },
    getData: function() {
      let items;
      axios
        .get("http://localhost:3000/getList")
        .then((res) => {
          items = res.data;
          console.log("Vue method called");
          console.log(res.data);
        })
        .catch((err) => console.log(err));
      return items;
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
  },
  created: function() {
    this.setData();
  },
};

// let test = function() {
//   axios
//     .get("http://localhost:3000/getList")
//     .then((res) => {
//       console.log(res.data);
//     })
//     .catch((err) => console.log(err));
// };

// test();

// const xhttp = new XMLHttpRequest();

// xhttp.open("GET", "http://localhost:3000/getList", false);
// xhttp.send();

// const books = JSON.parse(xhttp.responseText);
// console.log(books);

// async function makeGetRequest() {
//   let res = await axios.get("http://localhost:3000/getList");

//   let data = res.data;
//   console.log(data);
// }
// makeGetRequest();

// axios
//   .get("http://localhost:3000/getList")
//   .then((res) => console.log(res.data))
//   .catch((err) => console.log(err));
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
