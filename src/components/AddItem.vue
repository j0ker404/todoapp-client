<template>
  <div id="add" class="card">
    <input type="text" v-model="itemText" />
    <input type="button" value="Add" v-on:click="addItem" />
    <p>
      <!-- {{ itemText }} -->
    </p>
  </div>
</template>

<script>
export default {
  name: "AddItem",
  data: function() {
    return {
      itemText: "",
    };
  },
  methods: {
    boom: () => {
      alert("boom");
    },
    addItem() {
      if (this.itemText.trim().length !== 0) {
        console.log(`${this.itemText}`);
        this.$emit("newItem", this.itemText);
      } else {
        console.log("empty string");
      }
    },
  },
};
</script>

<style scoped>
#add.card {
  text-align: center;
  display: flex;
  flex-direction: column;
  /* padding: 0; */
  justify-content: space-around;

  /* padding:  */
}
.card {
  /* padding: 10px; */
  margin: auto 20px;
  height: auto;
  /* border-style: solid;
  border-width: 5px; */

  box-shadow: 1px 1px #dbceb9;
}

.card {
  /* border: 10px solid black; */
  background-color: rgb(242, 250, 250);
  height: inherit;
  padding: 1.1em 2em;
  /* padding: 1.1em 0; */
  margin: 1.1em 2em;

  box-shadow: 10 4px 28px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  /* width: 40%; */
  border-radius: 5px;
  /* text-align: center; */
}

.card:hover {
  box-shadow: 0 8px 16px 10px rgba(0, 0, 0, 0.2);
}
.card p.text {
  text-align: justify;
  width: inherit;
}

.card-img-prop {
  height: inherit;

  /* border-radius: 5px 5px 0 0; */
}
.card-img {
  height: 5em;
  width: 100%;
  text-align: center;
  /* border: 1px solid black;
  background-color: bisque; */
}

@media screen and (min-width: 769px) {
  .card {
    /* border: 10px solid black; */
    background-color: rgb(242, 250, 250);
    height: inherit;
    /* padding: 1.1em 2em; */
    margin: 1.1em auto;
    max-width: 75%;

    box-shadow: 10 4px 28px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    /* width: 40%; */
    border-radius: 5px;
    text-align: center;
  }
}

@media screen and (max-width: 320px) {
  .card {
    /* border: 10px solid black; */
    background-color: rgb(242, 250, 250);
    height: inherit;
    padding: 1.1em 2em;
    /* margin: 1.1em 2em; */
    /* margin: 0 auto; */

    box-shadow: 10 4px 28px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    /* width: 40%; */
    border-radius: 5px;
    text-align: center;
  }
}
</style>
