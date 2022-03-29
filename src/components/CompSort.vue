<template>
  <div class="col-12">
    <b-form-group>
      <b-dropdown id="dropdown-1" text="Sort by" class="dropdown">
        <b-dropdown-item @click="handleSort('name','asc')"><a class="dropdown-item" href="#">Name ASC</a></b-dropdown-item>
        <b-dropdown-item @click="handleSort('name','desc')"><a class="dropdown-item" href="#">Name DESC</a></b-dropdown-item>
        <b-dropdown-divider></b-dropdown-divider>
        <b-dropdown-item @click="handleSort('level','asc')"><a class="dropdown-item" href="#">Level ASC</a></b-dropdown-item>
        <b-dropdown-item @click="handleSort('level','desc')"><a class="dropdown-item" href="#">Level DESC</a></b-dropdown-item>
      </b-dropdown>
      <b-badge variant="success" class="order badge-medium">{{orderBy}} - {{orderDir}}</b-badge>
    </b-form-group>
  </div>
</template>

<script>
export default {
  name: "CompSort",
  props: {
    orderBy: String,
    orderDir: String
  },
  methods: {
    handleSort(orderBy, orderDir){
      this.$emit('handleSort', orderBy, orderDir);
    }
  }
}
</script>

<style scoped>
  .order{
    text-transform: uppercase;
  }
</style>