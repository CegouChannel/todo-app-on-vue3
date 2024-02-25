<template>
  <div>
    <input @keyup.enter="addTask" class="input" type="text" :placeholder="'Add a new task insdie ‘' + category + '’'" :value="value" @input="value = $event.target.value">
  </div>
</template>

<script>
export default {
  data () {
    return {
      value: ''
    }
  },
  props: {
    category: {
      type: String,
      required: true
    }
  },
  methods: {
    addTask () {
      let category = this.category
      if (this.value === '') {
        alert('Пустое поле!')
        return
      }
      if (this.category === 'All') {
        category = 'Uncategorized'
      }
      this.$emit('addTask', { category: category, value: this.value })
      this.value = ''
    }

  }
}
</script>

<style scoped>
  .input{
    outline: none;
    background: #F3F3F3;
    padding-left: min(1.7vw, 27px);
    color: #B5B5B5;
    font-size: min(1.1vw, 18px);
    height: min(3vw, 47px);
    border-radius: min(0.5vw, 8px);
    width: 100%;
    border: none;
  }
</style>
