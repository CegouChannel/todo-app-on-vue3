<template>
    <div class="content_taskUI">
        <div class="task">
          <input @click="$emit('updateStatus', this.task.id)" class="checkbox" type="checkbox" :checked="task.status">
          <h3>{{ task.task }}</h3>
          <div>{{ task.category }}</div>
        </div>
        <div>
          <img @click="$emit('deleteTask', task.id)" src="@/assets/image/delete_task.png" alt="delete_task">
        </div>
    </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.content_taskUI{
  display: flex;
  justify-content: space-between;
}
.task {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: start;
}

.task:not(:last-child){
  margin-bottom: min(1vw, 16px);
}

.task > h3 {
  margin-left: min(1.1vw, 18px);
  font-size: min(1.1vw, 18px);
  color: #5A5A5A;
  font-weight: 400;
}

.task > div{
  width: min(7.1vw, 115px);
  height: min(1.5vw, 24px);
  background: #EA5959;
  color: #fff;
  text-align: center;
  border-radius: 4px;
  font-size: min(0.75vw, 12px);
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: min(1.1vw, 18px);
}

input {
  outline: none;
  border-color: 1px solid #EA5959;
  background: none;
  height: min(1.75vw, 28px);
  width: min(1.75vw, 28px);
  border-radius:1px;
  border: none;
}

input:checked{
  background: #EA5959;
}
</style>
