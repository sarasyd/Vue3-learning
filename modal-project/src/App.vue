<template>
<h1>{{title}}</h1>
<p>Welcome...</p>
<teleport to="#modals" v-if="showModal">
  <Modal theme="" @close="toggleModal">
    <template v-slot:links>
      <a href="#">sign up now</a>
      <a href="#">more info</a>
    </template>
    <h1>Ninja Gaveway!</h1>
    <p>Grab your ninja swag for half price!</p>
  </Modal>
</teleport>
<teleport to="#modals" v-if="showModal2">
    <Modal  @close="toggleModal2">
    <h1>Signup to the nesletter</h1>
    <p>For updates and promo codes</p>
  </Modal>
</teleport>
<button @click="toggleModal">open modal</button>
<button @click="toggleModal2">open modal2</button>




</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components:{ Modal },
  data(){
    return{
      title:'My First Vue App :)',
      header:'sign up for the giveway',
      text:'Grab your ninja swag for half price!',
      showModal:false,
      showModal2:false,
    }
  },
  methods:{
toggleModal(){
  this.showModal=!this.showModal;
},
toggleModal2(){
  this.showModal2=!this.showModal2;
}
  }
}
</script>

<style>
#app, #modals{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
