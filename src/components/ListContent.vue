<template>
  <div id="lsContent">
    <!-- <ListItem v-bind:itemData="data[2]"/> -->
    <div v-for="item in data" v-bind:key="item.id">
        <ListItem v-bind:itemData="item"/>
    </div>
  </div>
</template>

<script>

import ListItem from './ListItem.vue'
export default {
    name: 'ListContent',
    components: {
      ListItem
    },

    props: ['data']
}
</script>

<style scoped>

</style>