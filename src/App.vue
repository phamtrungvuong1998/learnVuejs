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
        <CompControl :orderDir="orderDir" :orderBy="orderBy" :strSearch="strSearch" @handleSearch="handleSearch" @handleClear="handleClear" @handleSort="handleSort"></CompControl>
        <!-- CONTROL (SEARCH + SORT + ADD) : END -->

        <!-- FORM : START -->
        <CompForm :isShowForm="isShowForm" @handleAddTask="handleAddTask()" @onClickAddNewTask="onClickAddNewTask" :taskSelected="taskSelected"></CompForm>
        <!-- FORM : END -->
      </div>

      <!-- LIST : START -->
      <ListTable :listTask="listTaskSort" @handleDelete="handleDelete" @handleEdit="handleEdit"></ListTable>

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
      listTask: listTask,
      isShowForm: false,
      strSearch: "",
      orderBy: "name",
      orderDir: "asc",
      taskSelected: null
    }
  },
  components:{
    ListTable,
    CompControl,
    CompForm
  },
  methods:{
    handleAddTask(){
        this.isShowForm = !this.isShowForm;
        this.taskSelected = null;
    },
    handleSearch(data){
        this.strSearch = data;
        console.log(this.strSearch);
    },
    handleClear(data){
      this.strSearch = data;
    },
    handleSort(orderBy, orderDir){
      this.orderBy = orderBy;
      this.orderDir = orderDir;
    },
    compareName(a, b){
      var numberSort = this.orderDir == 'asc' ? -1 : 1;
      if (a.taskName < b.taskName) return numberSort;
      else if (a.taskName > b.taskName) return numberSort * (-1);
      return 0;
    },
    compareLevel(a, b){
      var levelSort = this.orderDir == 'asc' ? -1 : 1;
      if (a.level < b.level) return levelSort;
      else if (a.level > b.level) return levelSort * (-1);
      return 0;
    },
    handleDelete(task){
      this.listTask = this.listTask.filter(item => item.id != task.id);
    },
    onClickAddNewTask(objTask){
      this.listTask.push(objTask);
      this.isShowForm = false;
    },
    handleEdit(task){
      // this.isShowForm = true;
      this.taskSelected = task;

    }
  },
  computed: {
    listTaskSearch(){
      var newItems = [];
      var strSearch = this.strSearch;
      newItems = this.listTask.filter( item => item.taskName.toLowerCase().includes(strSearch.toLowerCase()) == true);
      return newItems;
    },
    listTaskSort(){
      var listTaskSort = [...this.listTaskSearch];
      if (this.orderBy == 'name'){
        listTaskSort.sort(this.compareName);
      }else if (this.orderBy == 'level'){
        listTaskSort.sort(this.compareLevel);
      }

      return listTaskSort;
    }
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
