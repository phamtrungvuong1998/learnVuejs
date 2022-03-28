<template>
  <div class="col-12 col-lg-6">
    <div class="row">
      <!-- SORT : START -->
      <CompSort></CompSort>
      <!-- SORT : END -->

      <!-- SEARCH : START -->
      <CompSearch></CompSearch>
      <!-- SEARCH : END -->
    </div>
  </div>
</template>

<script>
import CompSort from "./CompSort.vue";
import CompSearch from "./CompSearch.vue";

export default {
  name: "CompControl",
  components:{
    CompSort,
    CompSearch
  }
}
</script>

<style scoped>

</style>