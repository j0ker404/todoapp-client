<template>
  <div id="list-item" class="card">
    <!-- <div class="content">
      <input  type="text" />
    </div>
    <div class="btn">
      <button>{{buttonType}}</button>
    </div>-->
    <div id="item" v-bind:class="{ completed: this.itemData.status }">
      {{ itemData.title }}
    </div>
    <div id="options">
      <div id="status">
        <input
          type="checkbox"
          name="checkbox"
          id="statusIndicator"
          v-model="itemData.status"
          v-on:click="updateStatus"
        />
      </div>
      <div id="remove">
        <input type="button" value="remove" v-on:click="remove" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ListItem",
  props: ["itemData"],
  methods: {
    remove: function() {
      // call back function that sends request to be removed to "ListContent"
      this.$emit("removeMe", this.itemData.id);
    },
    updateStatus: function() {
      // call back function that sends request to be updateStatus to "ListContent"
      this.$emit("updateStatus", {
        id: this.itemData.id,
      });
    },
  },
};
</script>

<style scoped>
#list-item {
  display: flex;
  /* margin: 0 auto; */
  flex-direction: row;
  /* width: 100%; */
  justify-content: space-around;
}

.completed {
  text-decoration: line-through;
}

#item {
  /* flex: 70%; */
  text-align: justify;
  width: 80%;
  padding: 10px 1em;
}

/* #status {
  flex: 50%;
}

#remove {
  flex: 50%;
} */

#status input[type="checkbox"] {
  padding: 5spx;
}
#options {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
}

.card {
  padding: 10px;
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
  margin: 1.1em 2em;

  box-shadow: 10 4px 28px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  /* width: 40%; */
  border-radius: 5px;
  text-align: center;
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
