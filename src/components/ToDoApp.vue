<template>
  <div class="container"> 
    <h1 class="text-center mt-5">My Vue To do App.</h1>

    <div class="d-flex mt-5">
      <input v-model="task" type="text" placeholder="Enter task" class="form-control" >
      <button @click="submitTask()" type="button" class="btn btn-success">Success</button>
    </div>

    <table class="table mt-5">
      <thead class="table-dark "> 
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Status</th>
          <th scope="col" class="text-center">#</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td style="width= 50% " :class="{'finished': task.status === 'Finished',
          'in-progress': task.status === 'In-progress'}">
            <span>
              {{task.name}}
            </span>
          </td>
          <td style="width= 30% ">
            <span @click="changeStatus(index)" class="pointer"
            :class="{'text-danger': task.status === 'To-do',
            'text-warning': task.status === 'In-progress',
            'text-success': task.status === 'Finished'}">
              
              {{task.status}}
            </span>
          </td>
          <td style="width= 10% ">
            <div @click="editTask(index)" class="text-center">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td style="width= 10% "> 
            <div @click="deleteTask(index)" class="text-center">
              <span class="fa fa-trash"></span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'ToDoApp',
  props: {
    msg: String
  },

  data(){
    return{
      task: '',
      editedTask: null,
      availableStatus: ['To-do', 'In-progress', 'Finished'],

      tasks: [
              {
                name: 'Learn JavaScript',
                status: 'To-do'
              },
              {
                name: 'Learn VueJs',
                status: 'To-do'
              },
              {
                name: 'Learn Development',
                status: 'To-do'
              }
            ]
          }
  },
  
  methods: {
    submitTask(){
      if(this.task.length === 0)return;

      if(this.editedTask === null){
          this.tasks.push({
            name: this.task,
            status: 'to-do'
          })}
          else{
            this.tasks[this.editedTask].name = this.task
            this.editedTask = null
          }
          this.task = ''   
        
    },

    deleteTask(index){
      this.tasks.splice(index, 1)
    },

    editTask(index){
      this.task = this.tasks[index].name
      this.editedTask = index
    },

    changeStatus(index){
      let newIndex = this.availableStatus.indexOf(this.tasks[index].status)
      if(++newIndex > 2) newIndex = 0  
      this.tasks[index].status = this.availableStatus[newIndex] 
    }
  }
}


</script>
<style scoped>
.pointer{
  cursor: pointer;
}
.finished{
  text-decoration: line-through;
  background-color: #bdecb6;
}
.in-progress{
  
  background-color: #FDFD96;
}
</style>