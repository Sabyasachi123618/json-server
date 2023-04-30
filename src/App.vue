<template>
  <PageHeader title="TO-DO-LIST" @button-clicked="handleClick"/>
  <div v-if="showForm">
  <AddTask @Add-Task="onAddTask"/>
</div>
  <TasksComp @button-clicked="deletePost" :tasks="tasks"/>
</template>

<script>
import PageHeader from './components/PageHeader.vue';
import TasksComp from './components/TasksComp.vue';
import AddTask from './components/AddTask.vue';
export default {
  name: 'App',
  components:{
    PageHeader,
    TasksComp,
    AddTask
},
  data(){
    return{
      tasks:[],
      showForm:false
    }
  },
  async created(){
    this.tasks=await this.fetchTasks();
  },
  methods:{
        // this.tasks = this.tasks.filter((task)=>task.id!=id)
        async deletePost(id) {
          const result = await fetch(`http://localhost:5000/tasks/${id}`, {
      method: 'DELETE'
    })
    if(result.status==200)
    {
      location.reload();
    }
  },
   async onAddTask(newTask)
    {
      const result = await fetch('http://localhost:5000/tasks', {
      method: 'POST',
      headers: {
      'Content-Type': 'application/json'
    },
  body: JSON.stringify(newTask)
})
  const data = await result.json();
  this.tasks=[...this.tasks,data];
    },
    handleClick()
    {
      this.showForm=!this.showForm;
    },
    async fetchTasks()
    {
      const result = await fetch("http://localhost:5000/tasks")
      const data = await result.json();
      return data;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  border: 3px solid black ;
}
</style>
