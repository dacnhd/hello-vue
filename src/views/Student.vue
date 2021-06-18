<template>
  <div id="app">
    <h1>{{message}}</h1>
    <button @click="changeMessage">ChangeMessage</button>

    <Table :columns="columns" :data="students"/>
  </div>
</template>

<script>
import Table from "../components/Table";

export default {
  name: 'Student',
  components:{
    Table
  },
  data:{
    students:[],
    columns: [
        {
          label: 'RollNumber',
          field: 'rollNumber',
        },
        {
          label: 'Full Name',
          field: 'fullName',
        },
        {
          label: 'Email',
          field: 'email',
        },
        {
          label: 'Status',
          field: 'status',
        },
        {
          label: 'Created At',
          field: 'createdAt',
        },
        {
          label: 'Status',
          field: 'status',
        },
      ]
  },
  props:{ //components
    message: {
      type: String
    }
  },
  mounted(){
    this.loadStudent()
  },
  methods:{
    changeMessage(){
      this.$emit('changeMessage')
    },
    loadStudent(){
      fetch('http://localhost:8081/api/v1/students')
          .then(response => response.json())
          .then(data => this.students = data);
    }
  }
}
</script>

<style scoped>
  .error{
    color: red;
  }
</style>