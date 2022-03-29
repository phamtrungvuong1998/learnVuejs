<template>
  <div class="col-12">
    <div class="input-group">
      <input :value="strSearch" v-on:input="handleSearch()" type="text" class="form-control" placeholder="Search for..." />
      <span class="input-group-append">
								<button class="btn btn-info" type="button" @click="handleClear">Clear!</button>
							</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "CompSearch",
  props: {
    strSearch: String
  },
  data(){
    return {

    }
  },
  methods: {
    handleSearch(){
      this.$emit('handleSearch', event.target.value);
    },
    handleClear(){
      this.$emit('handleClear', "");
    }
  }
}
</script>

<style scoped>

</style>