<template>
<div id="app">
<h3>Passengers:</h3>
  <table class="table">
      <thead>
        <tr>
          <th scope="col">Id</th>
          <th scope="col">Survived</th>
          <th scope="col">class</th>
          <th scope="col">Name</th>
          <th scope="col">Sex</th>
          <th scope="col">Age</th>         
          <th scope="col">Siblings</th>
          <th scope="col">Parch</th>
          <th scope="col">Ticket</th>
          <th scope="col">Fare</th>
          <th scope="col">Cabin</th>
          <th scope="col">Embarked</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="passenger in passengers" v-bind:key="passenger.id"> 
          <th scope="row">{{passenger.id}}</th>
          <td>{{passenger.Id}}</td>
          <td>{{passenger.Survived}}</td>
          <td>{{passenger.class}}</td>
          <td>{{passenger.Name}}</td>
          <td>{{passenger.Sex}}</td>
          <td>{{passenger.Age}}</td>
          <td>{{passenger.Siblings}}</td>
          <td>{{passenger.Parch}}</td>
          <td>{{passenger.Ticket}}</td>
          <td>{{passenger.Fare}}</td>
          <td>{{passenger.Cabin}}</td>
          <td>{{passenger.Embarked}}</td>

        </tr>
      </tbody>
  </table>
</template>
<script>
 import axios from 'axios';
  export default {
    name: 'Passengers',
    data(){
      return{
        Passengers:[],
      };
    },
    created: function() {
      axios
        .get('http://coding-task.strakertranslations.com/passengers')
        .then(res => {
          this.Passengers = res.data;
        })
    }
  }
</script>
<style>
  h3 {
    margin-bottom: 5%;
  }
</style>