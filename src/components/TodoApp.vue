<template>
  <div class='container'>
    <h2>My Vue TodoApp</h2>

    <v-sheet width="300">
    <v-form @submit.prevent>
      <v-text-field
        v-model="task"
        label="Enter task"
      ></v-text-field>
      <v-btn @click="submitTask" block class="mt-2">SUBMIT</v-btn>
    </v-form>
  </v-sheet>

    <v-table
    fixed-header
    height="300px"
  >
    <thead>
      <tr>
        <th class="text-left">
          Task
        </th>
        <th class="text-left">
          Status
        </th>
        <th class="text-left">
          na
        </th>
        <th class="text-left">
          na
        </th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="(task, index) in tasks" :key="index">
        <td :class="{ 'completed': task.status === 'completed'}">{{ task.name }}</td>
        <td @click="changeStatus(index)" class="pointer" 
        :class="{'text-danger': task.status === 'to-do',
        'text-warning': task.status === 'in-progress',
        'text-success': task.status === 'completed'}" 
        style="width: 120px">{{ firstCharUpper(task.status) }}</td>
        <td class="text-left">
          <v-btn @click="editTask(index)">EDIT</v-btn>
        </td>
        <td class="text-left">
          <v-btn @click="deleteTask(index)">DELETE</v-btn>
        </td>
      </tr>
    </tbody>
  </v-table>
  </div>
</template>

<script>
export default {
    data () {
      return {
        task: '',
        editedTask: null,
        availableStatuses: ['to-do', 'in-progress', 'completed'],

        tasks: [
          {
            name: 'Buy chocolate ice cream',
            status: 'to-do',
          },
          {
            name: 'Participate in a marathon run',
            status: 'to-do',
          },
        ],
      }
    },

    methods: {
      submitTask() {
        if(this.task.length === 0) return;

        if(this.editedTask === null) {
          this.tasks.push({
          name: this.task,
          status: 'to-do',
        });
      } else {
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }
        this.task = '';
      },

      deleteTask(index) {
        this.tasks.splice(index, 1);
      },

      editTask(index) {
        this.task = this.tasks[index].name;
        this.editedTask = index;
      },

      changeStatus(index) {
        let newIndex = this.availableStatuses.indexOf(this.tasks[index].status);
        if(++newIndex > 2) newIndex = 0;
        this.tasks[index].status = this.availableStatuses[newIndex];
      },

      firstCharUpper(str){
        return str.charAt(0).toUpperCase() + str.slice(1);
      }
    }
};

</script>

<style scoped>
.pointer {
  cursor: pointer;
}
.completed {
  text-decoration: line-through;
}
</style>