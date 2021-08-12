<template>
<div class="container">
 <div class="card">

 <table  width="100%" >
  <tr>
    <th>ID</th>
    <th>Date de création</th>
    <th>Etat</th>
     <th>Nom</th>
    <th>Prénom</th>
    <th>Nom d'utilisateur</th>
     <th>Matricule</th>
    <th>Action</th>
  </tr>
  <tr v-for="user in users"  :key="user.id" class="tr">
   
    <td>{{user.id}}</td>
     <td>{{user.createdDate  | formatDate}}</td>
     <td><button type="button" class="btn " :class="getClass(user)" >
          {{user.status}}
     </button>
        </td>
    <td>{{user.lastName}}</td>
    <td>{{user.firstName}}</td>
    <td>{{user.status}}</td>
    <td>{{user.registrationNumber}}</td>
     <td><a @click="deleteUser(user)"><i class="far fa-trash-alt"></i></a></td>
  </tr>
</table>
</div>
 <Modal @newUser="addUser"></Modal>
<div  class="card">

<div class="row">
<div class="col-9"></div>
<div class="col ">
<button type="button" class="btn btn-warning" data-toggle="modal" data-target="#exampleModalCenter" >
 Ajouter un utilisateur
</button>
</div>
</div>

</div>
 
</div>
</template>

<script>
import Modal from './Modal.vue';
  import moment from 'moment';
  import Vue from 'vue';

Vue.filter('formatDate', function(value) {
    if (value) {
        return moment(String(value)).format('DD/MM/YYYY')
    }
});
export default {
 data(){
 return{
  users: [
  {
    id: "123456789",
    createdDate: "2021-01-06T00:00:00.000Z",
    status: "En validation",
    firstName: "Mohamed",
    lastName: "Taha",
    userName: "mtaha",
    registrationNumber: "2584",
  },
   {
    id: "987654321",
    createdDate: "2021-07-25T00:00:00.000Z",
    status: "Validé",
    firstName: "Hamid",
    lastName: "Orrich",
    userName: "horrich",
    registrationNumber: "1594",
  },
     {
    id: "852963741",
    createdDate: "2021-09-15T00:00:00.000Z",
    status: "Rejeté",
    firstName: "Rachid",
    lastName: "Mahidi",
    userName: "rmahidi",
    registrationNumber: "3576",
  }
]
 }
 },
  methods: {
    addUser (e) {
     this.users.push(e)
    },
    deleteUser(user){
     this.users.splice(this.users.indexOf(user), 1);
    },
     getClass(user){
         var classed="";
         if (user.status.includes("Validé")){
            classed='valide'
         }
         else if(user.status.includes("Rejeté")){
             classed='rejected'
         }
         else{
           classed='on-validation'
         }
       return classed;
  },

  },
  components:{
    Modal
  }
}
</script>


<style>
.tr {
  border-top: 1px solid #dddddd;
 
}
th,td{
 text-align: left;
  padding: 8px;
}
.card{
    margin-top: 50px;
}

.col button{
 margin: 5px !important;
   float:right
}
.valide {
  background-color: #5BE881;
}
.rejected {
  background-color: #FF0000;
}
.on-validation {
  background-color: #FDB64D;
}
</style>