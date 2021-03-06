<template>
  <div class="container center">
    <div class="row">
      <div class="col s8 offset-s2">
        <nav class="navbar blue" style='margin:0'>
          <h5 class="brand-logo center" style="font-family:'Stick',sans-serif">Task Tracker</h5>
        </nav>
      </div>
    </div>
    <Task v-for='task in tasks' :task='task' v-bind:key='task.id' @deleteme="deleteme"/> 
    <div class="row">
      <div class="col s8 offset-s2 input-field">
        <label for="newtask">Create new task</label>
        <input type="text" name="" id="newtask" v-model='taskvalue'>
      </div>
    </div>
    <a class="btn-floating btn-large waves-effect waves-light blue" @click='addTask'><i class="material-icons">add</i></a>
  </div>
</template>

<script>

// ---  Import statements Here
import Task from './components/Task'
// ---

export default {
  name: 'App',
  components: {
    Task
  },
  methods:{
    deleteme(id){
      console.log(id);
      this.tasks = this.tasks.filter(x=>{
        if(x.id != id){
          return x;
        }
      })
    },
    addTask(){
      var task = {
        id:this.tasks.length + 1,
        content:this.taskvalue,
        date:'Random Date'
      }
      this.tasks.push(task)
    }
  },
  data(){
    return{
      taskvalue:'',
      tasks:[
        {
          id:1,
          content:'Buy Veggies',
          date:'4th March'
        },
        {
          id:2,
          content:'Buy Eggs',
          date:'8th March'
        }
      ]
    }
  }
}
</script>

<style>
</style>
