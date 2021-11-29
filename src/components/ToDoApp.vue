<template>
  <div class="container"> 
    <h1 class="text-center mt-5">My Vue To do App.</h1>

    <div class="d-flex mt-5">
      <input type="text" placeholder="Enter task" class="form-control" >
      <button type="button" class="btn btn-success">Success</button>
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
        <tr v-for="(task, index) in task" :key="index">
          <td >{{task.name}}</td>
          <td>{{task.status}}</td>
          <td>
            <div class="text-center">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center">
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
      task: [
              {
                name: 'Learn JavaScript',
                status: 'To do'
              },
              {
                name: 'Learn VueJs',
                status: 'To do'
              },
              {
                name: 'Learn Development',
                status: 'To do'
              }
            ]
          }
  }    
}

</script>
<style scoped>

</style>