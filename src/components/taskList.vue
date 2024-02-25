<template>
  <div v-if="dataTasks.length > 0">
    <transition-group name="list" tag="p">
      <taskUI @updateStatus="updateStatus" @deleteTask="send" v-for="task in dataTasks" :key="task.id" :task="task"/>
    </transition-group>
  </div>
  <h4 v-else>
    There are no tasks
  </h4>
</template>

<script>
import taskUI from '@/components/UI/taskUI.vue'

export default {
  components: {
    taskUI
  },

  props: {
    dataTasks: {
      type: Array,
      required: true
    }
  },
  methods: {
    send (data) {
      this.$emit('deleteTask', data)
    },

    updateStatus (data) {
      this.$emit('updateStatus', data)
    }
  }
}
</script>

<style scoped>
.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-enter-active,
.list-leave-active {
  transition: all 0.3s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(130px);
}
</style>
