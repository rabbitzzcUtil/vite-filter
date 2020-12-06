<template>
    <div>
        <h1>CSS FILTER</h1>
        <Filter></Filter>
    </div>
</template>

<script>

import Filter from './components/filterComponents.vue'
export default {
  name: 'App',
  components: {
      Filter
  }
}
</script>

<style scoped>
h1 {
    text-align: center;
}
</style>
