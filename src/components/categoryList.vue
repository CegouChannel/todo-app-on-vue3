<template>
  <div>
    <ul>
      <li @click="this.$emit('selectCategory', category.name)" v-for="category in categories" :key="category.id">{{ category.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    categories: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
ul{
  list-style: none;
  color: #525252;
  font-size: min(1.3vw, 22px);
  margin-bottom: min(1.5vw, 24px);
  font-weight: bold;
}

li{
  margin-bottom: min(1.5vw, 24px);
  transition: .3s;
}

li:hover{
  color: #EA5959;
  transition: .3s;
}
</style>
