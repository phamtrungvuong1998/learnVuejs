<template>
  <div class="col-12 col-lg-6">
    <!-- ADD : START -->
    <div class="form-group add-task">
      <button type="button" class="btn btn-info btn-block" @click="onClickAddTask()" v-if="!isShowForm">Add Task</button>
      <button type="button" class="btn btn-info btn-block" @click="onClickAddTask()" v-if="isShowForm">Close Task</button>
    </div>
    <!-- ADD : END -->

    <form action="" method="POST" class="form-inline justify-content-between" v-if="isShowForm">
      <div class="form-group">
        <input v-model="taskName" type="text" class="form-control" placeholder="Task Name" />
      </div>
      <div class="form-group">
        <select name="ds" class="form-control" required="required" v-model="level">
          <option value="0">Small</option>
          <option value="1">Medium</option>
          <option value="2">High</option>
        </select>
      </div>

      <button type="button" class="btn btn-primary" @click="onClickAddNewTask">Submit</button>
      <button type="button" class="btn btn-secondary" @click="onClickAddTask()">Cancel</button>
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
  name: "CompForm",
  props:{
    isShowForm: {
      type: Boolean,
      default: false
    },
    taskSelected: {
      type: Object,
      default: null
    }
  },
  methods:{
    onClickAddTask(){
      this.$emit('handleAddTask');
    },
    onClickAddNewTask(){
      if (this.taskName == ""){
        alert("Vui lòng điền name");
      }else{
        var objTask = {
          id : uuidv4(),
          taskName : this.taskName,
          level : this.level
        }
        this.$emit('onClickAddNewTask', objTask);
        this.taskName = "";
        this.level = 0;
      }
    }
  },
  data(){
    return {
      taskName: "",
      level: 0
    }
  },
  beforeUpdate() {
    console.log(this.taskSelected);
  }
}
</script>

<style scoped>

</style>