<template>
  <div id="app">
    <div class="content">
      <categoreList class="categoryList" @selectCategory="selectCategory" :categories="categories"/>
      <pageCategory @updateStatus="updateStatus" @addTask="addTask" @deleteTask="deleteTask" class="pageCategory" :dataTasks="getTasks()" :category="selectedCategory"/>
    </div>
  </div>
</template>

<script>
import categoreList from '@/components/categoryList.vue'
import pageCategory from '@/components/pageCategory.vue'

export default {
  components: {
    categoreList, pageCategory
  },
  data () {
    return {
      dataTasks: [
        { id: 1, category: 'Groceries', task: 'Purchase Milk & Corn Flakes', status: false },
        { id: 2, category: 'College', task: 'Complete Assignments', status: false },
        { id: 3, category: 'Payments', task: 'Pay mortgage', status: false },
        { id: 4, category: 'Uncategorized', task: 'Get a new helmet', status: false },
        { id: 5, category: 'Uncategorized', task: 'Replace laptop\'s screen', status: false }
      ],
      categories: [
        { id: 1, name: 'All' },
        { id: 2, name: 'Groceries' },
        { id: 3, name: 'College' },
        { id: 4, name: 'Payments' }
      ],
      selectedCategory: 'All'
    }
  },
  methods: {
    selectCategory (newValue) {
      this.selectedCategory = newValue
    },

    getTasks () {
      if (this.selectedCategory === 'All') {
        return this.dataTasks
      } else {
        const response = this.dataTasks.filter(task => task.category === this.selectedCategory)
        return response
      }
    },
    deleteTask (id) {
      this.dataTasks = this.dataTasks.filter(task => task.id !== id)
      console.log(this.dataTasks)
    },
    addTask (data) {
      let id = 1
      if (this.dataTasks.length > 0) {
        const lastTask = this.dataTasks[this.dataTasks.length - 1]
        id = lastTask.id + 1
      }
      const newTask = {
        id: id,
        category: data.category,
        task: data.value,
        status: false
      }
      this.dataTasks.push(newTask)
    },
    updateStatus (id) {
      let task
      for (task of this.dataTasks) {
        if (task.id === id) {
          if (task.status === false) {
            task.status = true
          } else {
            task.status = false
          }
        }
      }
    }
  }
}
</script>

<style>
@font-face {
  font-family: 'Lato';
  src: url('@/assets/fonts/Lato-Regular.ttf');
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Lato';
}
#app {
  width: 100%;
  height: 100vh;
  background: #EA5959;
  display: flex;
  justify-content: center;
  align-items: center;
}

.content {
  background: #fff;
  width: min(61vw, 983px);
  height: min(43vw, 702px);
  border-radius: min(0.5vw, 8px);
  filter: drop-shadow(0px 10px 10px rgba(0, 0, 0, 0.25));
  display: flex;
}

.categoryList{
  width: min(13vw, 209px);
  display: flex;
  justify-content: center;
  padding-top: min(8.6vw, 139px);
  border-right: 1px solid #D8D8D8;
}

.pageCategory{
  width: 100%;
  padding-top: min(1.8vw, 30px);
  padding-left: min(3.3vw, 53px);
  padding-right: min(3.3vw, 53px);
}
</style>
