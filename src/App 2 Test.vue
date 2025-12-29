<script>

export default {
 data() {
  return {
  message: "Hello Vue!",
  status: "pending",
  tasks: ['Task One', 'Task Two', 'Task Three'],
  link: "https://vuejs.org",
  newTask: "",
  };
 },
 methods: {
  togglestatus() {
   if (this.status === "active") {
    this.status = "inactive";
   } else if (this.status === "inactive") {
    this.status = "pending";
   } else {
    this.status = "active";
   }
  },
  addTask() {
   if (this.newTask.trim() !== ''){
      this.tasks.push(this.newTask);
      this.newTask = '';
   }
  }
 },
 // Use a property assignment for mounted so parsers don't complain
 mounted: async function() {
  try {
   const res = await fetch('https://jsonplaceholder.typicode.com/todos');
   const data = await res.json();
   if (Array.isArray(data)) this.tasks = data.map(t => t.title);
   else if (data && data.title) this.tasks = [data.title];
  } catch (err) {
   console.error('Error fetching tasks:', err);
  }
 }
};
</script>
<template>
 <h1>{{ message }}</h1>
 <p v-if="status === 'active'">USER IS ACTIVE</p>
 <p v-else-if="status === 'pending'">USER IS PENDING</p>
 <p v-else>USER IS INACTIVE</p>
<form @submit.prevent="addTask">
   <label for="newTask">Add Task</label>
   <input type="text" name="newTask" id="newTask" v-model="newTask">
   <button type="submit">Submit</button>
</form>
 <h3>Tasks:</h3>
 <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
 </ul>
    <a :href="link" target="_blank">Vue.js Official Website</a>
    <br/>
    <button v-on:click="togglestatus">Change Status</button>
</template>

