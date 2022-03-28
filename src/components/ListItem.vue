<template>
  <tr>
    <td class="text-center">{{index}}</td>
    <td>{{task.taskName}}</td>
    <td class="text-center"><span class="badge" :class="classLevel">{{ getLevelName }}</span></td>
    <td>
      <button type="button" class="btn btn-warning">Edit</button>
      <button type="button" class="btn btn-danger">Delete</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "ListItem",
  props: {
    task: {
      type: Object,
      default: null
    },
    index: Number,
  },
  computed: {
    getLevelName(){
      switch (this.task.level){
        case 0:
          return 'Small';
        case 1:
          return "Medium";
        case 2:
          return  "High";
        default:
          return "";
      }
    },
    classLevel(){
      switch (this.task.level){
        case 0:
          return {"badge-danger" : true};
        case 1:
          return {"badge-success" : true};
        case 2:
          return {"badge-secondary" : true};
        default:
          return {};
      }
    }
  },
  data(){
    return {

    }
  },
}
</script>

<style scoped>

</style>