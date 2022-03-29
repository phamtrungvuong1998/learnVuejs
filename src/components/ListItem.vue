<template>
  <tr>
    <td class="text-center">{{index}}</td>
    <td>{{task.taskName}}</td>
    <td class="text-center"><span class="badge" :class="classLevel">{{ getLevelName }}</span></td>
    <td>
      <button type="button" class="btn btn-warning" @click="handleEdit">Edit</button>
      <button type="button" class="btn btn-danger" @click="handleDelete">Delete</button>
    </td>
  </tr>
</template>

<script>
import mapLevel from "../mocks/level.js";
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
      return this.mapLevel[this.task.level].level;
    },
    classLevel(){
      return this.mapLevel[this.task.level].classLevel;
    }
  },
  data(){
    return {
      mapLevel: mapLevel
    }
  },
  methods: {
    handleDelete(){
      this.$emit('handleDelete', this.task);
    },
    handleEdit(){
      this.$emit('handleEdit', this.task);
    }
  }
}
</script>

<style scoped>

</style>