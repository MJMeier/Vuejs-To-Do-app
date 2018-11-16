<template>
  <div class="home">
    <h1>Mike's To Do List!! ..whoa..</h1>
    <div>
       Purpose: <input type="text" v-model="newTaskPurpose">
       Priority: <input type="text" v-model="newTaskPriority">
       Text: <input type="text" v-model="newTaskText">
       <button v-on:click="createTask()">Create!</button>
     </div>
    <h1>tasks</h1>
    <div v-for="task in tasks">
      <h3 v-on:click="destroyTask(task)">{{ task.purpose }} - {{ task.priority }}</h3>
     <p>{{ task.text }}</p>
   </div>
 </div>
</template>

<style>
</style>

<script>
  export default {
    data: function() {
      return {
        message: "Mike's To Do List!!! ..whoa..",
        newTaskPurpose: "",
        newTaskPriority: "",
        newTaskText: "",
        tasks: [
          {
            id: 1,
            text: "Stop being Sick :("  ,
            priority: 1000000,
            purpose: "To feel Better :)"
          },
          {
            id: 2,
            text: "Become the best programmer ever",
            priority: 30000,
            purpose: "To make mucho dinero"
          },
          {
            id: 3,
            text: "Laundry, boring",
            priority: 1,
            purpose: "eh, cause i have to"
          }
        ]
      };
    },
    created: function() {},
    methods: {
      createTask: function() {
        if (this.newTaskText !== "") {
          var newTask = {
            id: 5,
            text: this.newTaskText,
            priority: this.newTaskPriority,
            purpose: this.newTaskPurpose
          };
          this.tasks.push(newTask);
          this.newTaskText = "";
          this.newTaskPriority = "";
          this.newTaskPurpose = "";
        }
      },
      destroyTask: function(inputtask) {
        console.log("destroyTask");
        var index = this.tasks.indexOf(inputtask);
        if (index > -1) {
          this.tasks.splice(index, 1);
        }
      }
    },
    computed: {}
  };
</script>         
