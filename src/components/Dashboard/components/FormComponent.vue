<template>

<div class="main-table">
  <p class="alert alert-danger" role="alert" v-if="errors.length">
    <b>Please correct the following error(s):</b>
    <ul>
      <li v-for="error in errors" :key="error.id" class="col-mb-2">{{ error }}</li>
    </ul>
  </p>
  <!-- <p div class="alert alert-success" role="alert" v-if="success.length">
    <ul>
     <li v-for="succes in success" :key="succes.id" class="col-mb-2">{{ succes }}</li>
    </ul>
  </p> -->

<form class="row g-3">
  <div class="col-md-2">
    <label for="inputEmail4" class="form-label">Nome</label>
    <input v-model="name" class="form-control" >
    
  </div>
  <div class="col-md-2">
    <label for="inputPassword4" class="form-label">Tipo</label>
     <select v-model="type" class="form-select">
      <option selected>1</option>
      <option>2</option>
      <option>3</option>
    </select>
  </div>
  <div class="col-2">
    <label for="inputAddress" class="form-label">Quartos</label>
    <input type="number" v-model="rooms" class="form-control" placeholder="1234 Main St" required>
  </div>
  <div class="col-2">
    <label for="inputAddress2" class="form-label">Suits</label>
    <input type="number" class="form-control" v-model="suits" placeholder="Apartment, studio, or floor" required>
  </div>
  <div class="col-md-2">
    <label for="inputCity" class="form-label">Cozinhas</label>
    <input type="number" class="form-control" v-model="kitchen" required>
  </div>
 
  <div class="col-md-2">
    <label for="inputZip" class="form-label">Sala</label>
    <input type="number" class="form-control" v-model="lRoom" required>
  </div>
  <div class="col-md-2">
    <label for="inputZip" class="form-label">WC</label>
    <input type="number" class="form-control" v-model="wc" required>
  </div>
  <div class="col-md-2">
    <label for="inputZip" class="form-label">Garagem</label>
    <input type="number" class="form-control" v-model="garage" required>
  </div>
  <div class="col-md-2">
    <label for="inputZip" class="form-label">Localizacao</label>
    <input type="text" class="form-control" v-model="location" required>
  </div>
  <div class="col-md-2">
    <label for="inputZip" class="form-label">Descricao</label>
    <input type="text" class="form-control" v-model="description" required>
  </div>
  <div class="col-md-2">
    <label for="inputZip" class="form-label">Preco</label>
    <input type="text" class="form-control" v-model="price" required>
  </div>
  <div class="col-md-2">
    <label for="inputZip" class="form-label">Visitas</label>
    <input type="date" class="form-control" v-model="visits" required>
  </div>
   <div class="col-md-2">
    <label for="inputState" class="form-label">Outdoor</label>
    <select v-model="outdoor" class="form-select" required>
      <option selected>1</option>
      <option>...</option>
    </select>
   </div>
   <div class="col-md-2">
    <label for="inputState" class="form-label">Promotion</label>
    <select v-model="promotion" class="form-select" required>
      <option selected>1</option>
      <option>...</option>
    </select>
  </div>
  <div class="col-md-2">
    <label for="inputZip" class="form-label">Preco em promocao</label>
    <input type="text" class="form-control" v-model="promotionPrice" required>
  </div>
  <div class="col-md-6">
    <label for="inputZip" class="form-label">Escolha as imagens</label>
    <input type="file" class="form-control" id="files" ref="files" multiple v-on:change="handleFilesUpload()" required>
  </div>
  
  <!-- <div class="col-12">
    <div class="form-check">
      <input class="form-check-input" type="checkbox" id="gridCheck">
      <label class="form-check-label" for="gridCheck">
        Check me out
      </label>
    </div>
  </div> -->

  <div class="col-12">
    <button type="submit" @click.prevent="salvar" class="btn btn-primary">Salvar</button>
  </div>
</form>
</div>

</template>

<script>
import axios from 'axios'

name: "FormComponent"

export default {
data(){
  return{
  name: '',
  type: '',
  rooms: '',
  suits: '',
  kitchen: '',
  lRoom: '',
  wc: '',
  garage: '',
  location: '',
  description: '',
  price: '',
  visits: '',
  outdoor: '',
  promotion: '',
  promotionPrice: '',
  image: '',
  files: [],
  errors:[],
  success:[]


  }
},

methods:{
  salvar(){
    this.errors = [];
    

    if (!this.name) {
        this.errors.push('Name required.');
      } 
      if (!this.type) {
        this.errors.push('type required.');
      }
      if (!this.rooms) {
        this.errors.push('Rooms required.');
      }
      if (!this.suits) {
        this.errors.push('suits required.');
      }
      if (!this.kitchen) {
        this.errors.push('kitchen required.');
      }
      if (!this.lRoom) {
        this.errors.push('Living Room required.');
      }
      if (!this.wc) {
        this.errors.push('Wc required.');
      }
      if (!this.garage) {
        this.errors.push('garage required.');
      }
      if (!this.location) {
        this.errors.push('location required.');
      }
      if (!this.price) {
        this.errors.push('price required.');
      }
      if (this.files.length < 4){
        this.errors.push('Pictures required.');
      }
      if (!this.errors.length) {

    let formData = new FormData();
   formData.append('name',this.name)
      formData.append('type',this.type)
      formData.append('rooms',this.rooms)
      formData.append('suits',this.suits)
      formData.append('kitchen',this.kitchen)
      formData.append('lRoom',this.lRoom)
      formData.append('wc',this.wc)
      formData.append('garage',this.garage)
      formData.append('location',this.location)
      formData.append('description',this.description)
      formData.append('price',this.price)
      formData.append('visits',this.visits)
      formData.append('outdoor',this.outdoor)
      formData.append('promotion',this.promotion)
      formData.append('promotionPrice',this.promotionPrice)

    for( var i = 0; i < this.files.length; i++ ){
    let file = this.files[i];

    formData.append('files[' + i + ']', file);
    console.log(file)
    }

    axios.post('http://127.0.0.1:8000/api/houses/newhouse', formData,
  {
    headers: {
        'Content-Type': 'multipart/form-data'
    }
  })
  .then(function (response) {
    console.log(response.data.msg);

    if (response.data.code < 400){
      alert(response.data.msg);      
    }
  })
  .catch(function (error) {
    console.log(error);
  });

        return true;  
      }
    },

   handleFilesUpload(){
        this.files = this.$refs.files.files;
      },
  }

}
</script>

<style lang="scss" scoped>
.validations{
  li{
    color: red;
  }
}
</style>