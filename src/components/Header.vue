<template>
  <div class="heading">
    <h1>{{title}}</h1>
  </div>
</template>

<script>
export default {
  name: "Heading",
  props: {
    title: String
  }
};
</script>

<style scoped>
.heading {
  margin: 40px 0;
  text-align: center;
}
</style>
