<template>
  <div id="app">
    <div class="container">

      <!-- TITLE : START -->
      <div class="page-header">
        <h1>Project 01 - ToDo List <small>VueJs</small></h1>
        <hr class="my-4">
      </div>
      <!-- TITLE : END -->


      <div class="row">
        <!-- CONTROL (SEARCH + SORT + ADD) : START -->
        <CompControl></CompControl>
        <!-- CONTROL (SEARCH + SORT + ADD) : END -->

        <!-- FORM : START -->
        <CompForm></CompForm>
        <!-- FORM : END -->
      </div>

      <!-- LIST : START -->
      <ListTable :listTask="listTask"></ListTable>

    </div>
  </div>
</template>

<script>
import ListTable from "./components/ListTable.vue";
import CompControl from "./components/CompControl.vue";
import CompForm from "./components/CompForm.vue";
import listTask from "./mocks/task.js";
export default {
  name: 'App',
  data(){
    return {
      listTask: listTask
    }
  },
  components:{
    ListTable,
    CompControl,
    CompForm
  }
}
</script>

<style>
.form-group {
  margin-bottom: 1rem;
}

body {
  padding: 100px 0;
}
.table>tbody>tr>td, .table>tbody>tr>th, .table>tfoot>tr>td, .table>tfoot>tr>th, .table>thead>tr>td, .table>thead>tr>th {
  vertical-align: middle;
}

.container > .row {
  margin-top: 20px;
  margin-bottom: 30px;
}

span.badge-medium {
  padding: 11px 10px;
  margin: 0px 8px;
  font-size: 16px;
  display: inline-block;
  vertical-align: top;
}

.badge-success {
  color: #fff;
  background-color: #28a745;
}
.btn-block {
  display: block;
  width: 100%;
}
.form-inline .form-control {
  display: inline-block;
  width: auto;
  vertical-align: middle;
}

.form-inline .form-group {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-flex: 0;
  -ms-flex: 0 0 auto;
  flex: 0 0 auto;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
  -ms-flex-flow: row wrap;
  flex-flow: row wrap;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  margin-bottom: 0;
}

.justify-content-between {
  justify-content: space-between !important;
}

.form-inline {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
  -ms-flex-flow: row wrap;
  flex-flow: row wrap;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
}

.badge-danger {
  color: #fff;
  background-color: #dc3545;
}

.badge-secondary {
  color: #fff;
  background-color: #6c757d;
}

.badge-info {
  color: #fff;
  background-color: #17a2b8;
}

@media (max-width: 992px) {
  .add-task {
    margin-top: 50px;
  }
}

</style>
