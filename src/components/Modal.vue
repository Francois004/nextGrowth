<template>
 <div>
  <div class="modal fade" id="exampleModalCenter" tabindex="-1" role="dialog" aria-labelledby="exampleModalCenterTitle" aria-hidden="true">
  <div class="modal-dialog modal-dialog-centered" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h4 class="modal-title" id="exampleModalCenterTitle">Ajout d'utilisateurs</h4>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
       <form>
  <div class="form-row">
    <div class="form-group col-md-6">
      <label for="name">Nom</label>
      <input type="text" class="form-control" id="" placeholder="" v-model="newuser.lastName">
    </div>
    <div class="form-group col-md-6">
      <label for="firstname">Prénom</label>
      <input type="text" class="form-control" id="" placeholder="" v-model="newuser.firstName">
    </div>
  </div>
  
  <div class="form-row">
   <div class="form-group col-md-6">
    <label for="status">Etat</label>
    <select id="inputState" class="form-control" v-model="newuser.status">
        <option >Validé</option>
        <option>En validation</option>
        <option>Rejeté</option>
      </select>
  </div>
  <div class="form-group col-md-6">
    <label for="username">Nom d'utilisateur</label>
    <input type="text" class="form-control" id="" placeholder=""  v-model="newuser.userName">
  </div>
  </div>
   <div class="form-group col-md-6">
      <label for="registration">Matricule</label>
      <input type="text" class="form-control" id="" v-model="newuser.registrationNumber">
    </div>

</form>
      </div>
      <div class="modal-footer">
       
        <button type="button" class="btn btn-warning" data-dismiss="modal"  @click="save" :disabled="newuser.firstName==''||newuser.lastName==''||newuser.username==''||newuser.status==''">Enregistrer</button>
      </div>
    </div>
  </div>
</div>

 </div>
</template>

<script>
export default {
 data(){

   return{

      newuser:{
     id: Math.floor(Math.random() * 1000000000),
    createdDate: new Date(),
    status: "",
    firstName: "",
    lastName: "",
    userName: "",
    registrationNumber: ""
          }

       }
    },
 methods:{
    save() {
     this.$emit('newUser',this.newuser)
   }
 }
}
</script>

<style>

</style>