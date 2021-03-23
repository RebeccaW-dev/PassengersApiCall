<template>
  <div id="app">
    <h3>Passengers:</h3>
    <table class="table">
      <thead>
          <tr>
              <th @click="sort('Id')">Id</th>  
              <th @click="sort('Survived')">Survived</th>  
              <th @click="sort('class')">class</th>  
              <th @click="sort('Name')">Name</th>  
              <th @click="sort('Sex')">Sex</th>  
              <th @click="sort('Age')">Age</th>  
              <th @click="sort('Siblings')">Siblings</th>  
              <th @click="sort('Parch')">Parch</th>
              <th @click="sort('Ticket')">Ticket</th>  
              <th @click="sort('Fare')">Fare</th>  
              <th @click="sort('Cabin')">Cabin</th>  
              <th @click="sort('Embarked')">Embarked</th>


          <!-- <th scope="col">Id</th>
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
          <th scope="col">Embarked</th> -->
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
    <div class="pagination">
        <button @click="prevPage">Previous</button>
        <button @click="nextPage">Next</button>
        </div>
    </div> 
</template>
<script>
  import axios from 'axios';
  export default {
    name: 'Passengers',
    data() {
        return {
        passengers:[],
        currentSort:'id',
        currentSortDir:'asc',
        pageSize:20,
        currentPage:1
        };
    },
    methods:{
        nextPage:function() {
        if((this.currentPage*this.pageSize) < this.passengers.length) this.currentPage++;
        },
        prevPage:function() {
        if(this.currentPage > 1) this.currentPage--;
    },


     sort:function(s) {

         if(s===this.currentSort) {
             this.currentSortDir=this.currentSortDir==='asc'?'desc':'asc';
         }
         this.currentSort=s
     }
    },
    computed:{
     sortedPassenger:function() {
     return this.passengers.sort((a,b) => {       // eslint-disable-line
      let modifier = 1;
      if(this.currentSortDir === 'desc') modifier = -1;
      if(a[this.currentSort] < b[this.currentSort]) return -1 * modifier;
      if(a[this.currentSort] > b[this.currentSort]) return 1 * modifier;
      return 0;
    });
  }
},
    created: function() {
      axios
        .get('http://coding-task.strakertranslations.com/passengers')
        .then(res => {
          this.passengers = res.data;
        })
    },
    
  }
  
</script>
<style>
  h3 {
    margin-bottom: 5%;
  }
</style>