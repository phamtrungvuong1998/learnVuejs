<template>
  <div class="col-12 col-lg-6">
    <div class="row">
      <!-- SORT : START -->
      <CompSort :orderBy="orderBy" :orderDir="orderDir" @handleSort="handleSort"></CompSort>
      <!-- SORT : END -->

      <!-- SEARCH : START -->
      <CompSearch :strSearch="strSearch" @handleSearch="handleSearch" @handleClear="handleClear"></CompSearch>
      <!-- SEARCH : END -->
    </div>
  </div>
</template>

<script>
import CompSort from "./CompSort.vue";
import CompSearch from "./CompSearch.vue";

export default {
  name: "CompControl",
  props: {
    strSearch: String,
    orderBy: String,
    orderDir: String
  },
  components:{
    CompSort,
    CompSearch
  },
  methods: {
    handleSearch(data){
      this.$emit('handleSearch', data);
    },
    handleClear(data){
      this.$emit('handleClear', data);
    },
    handleSort(orderBy, orderDir){
      this.$emit('handleSort', orderBy, orderDir);
    }
  }
}
</script>

<style scoped>

</style>