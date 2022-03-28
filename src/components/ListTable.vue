<template>
  <div class="panel panel-success">
    <div class="panel-heading">List Task</div>
    <table class="table table-hover ">
      <thead>
      <tr>
        <th style="width: 10%" class="text-center">#</th>
        <th>Task</th>
        <th style="width: 20%" class="text-center">Level</th>
        <th style="width: 160px">Action</th>
      </tr>
      </thead>

      <tbody>
        <ListItem v-for="(task, index) in listTask" :key="index" :task="task" :index="index + 1"></ListItem>
      </tbody>

    </table>
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";

export default {
  name: "ListTable",
  props: {
    listTask: {
      type: Array
    }
  },
  data(){
    return {

    }
  },
  components:{
    ListItem
  }
}
</script>

<style scoped>

</style>