<template>
  <div class="col-12">
    <b-form-group>
      <b-dropdown id="dropdown-1" text="Sort by" class="dropdown">
        <b-dropdown-item><a class="dropdown-item" href="#">Name ASC</a></b-dropdown-item>
        <b-dropdown-item><a class="dropdown-item" href="#">Name DESC</a></b-dropdown-item>
        <b-dropdown-divider></b-dropdown-divider>
        <b-dropdown-item><a class="dropdown-item" href="#">Level ASC</a></b-dropdown-item>
        <b-dropdown-item><a class="dropdown-item" href="#">Level DESC</a></b-dropdown-item>
      </b-dropdown>
      <b-badge variant="success" class="badge-medium">NAME - DESC</b-badge>
    </b-form-group>
  </div>
</template>

<script>
export default {
  name: "CompSort"
}
</script>

<style scoped>

</style>