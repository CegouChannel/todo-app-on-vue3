<template>
  <div>
      <h3>{{ category }} Tasks</h3>
      <inputUI @addTask="addTask" class="inputTask" :category="category"/>
      <taskList @updateStatus="updateStatus" @deleteTask="deleteTask" class="tasksList" :dataTasks="dataTasks"/>
  </div>
</template>

<script>
import inputUI from '@/components/UI/inputUI.vue'
import taskList from '@/components/taskList.vue'
export default {
  components: {
    inputUI, taskList
  },
  props: {
    dataTasks: {
      type: Array,
      required: true
    },
    category: {
      type: String,
      required: true
    }
  },
  methods: {
    deleteTask (data) {
      this.$emit('deleteTask', data)
    },
    addTask (data) {
      this.$emit('addTask', data)
    },
    updateStatus (data) {
      this.$emit('updateStatus', data)
    }
  }
}
</script>

<style scoped>
h3{
  font-size: min(2vw, 32px);
  color: #000;
  font-weight: 700;
  margin-bottom: min(1.5vw, 25px);
}

.inputCategory{
  margin-bottom: min(2vw, 32px);
}

.inputTask{
  margin-bottom: min(2vw, 32px);
}
</style>
