<template>
  <div id="app">
    <h3>Cadastro:</h3>
    <input type="text" placeholder="nome" v-model="nomeField"><br>
    <input type="email" placeholder="email" v-model="emailField"><br>
    <input type="number" placeholder="idade" v-model="idadeField"><br>
    <button @click="adicionarCliente">Adicionar cliente</button>

    <div v-for="(cliente,index) in clientesOrdenados" :key="cliente.id">
      <h1>{{ index + 1}}</h1>
      <Cliente :cliente="cliente" @meDelete="deletarUsuario($event)"/>
      <h4>Edição: </h4>
      <input type="text" v-model="cliente.nome">
      <input type="text" v-model="cliente.email">
      <hr>

    </div>
  </div>
</template>

<script>
import Cliente from './components/Cliente'
//import Produto from './components/Produto'
import _ from 'lodash'

export default {
  name: 'App',
  data(){
    return {
      nomeField: '',
      emailField: '',
      idadeField: 0,
    clientes: [
      {
        id:1,
        nome: 'Jim',
        email: 'jim@gmail.com',
        idade: 35
    },
    {
        id:2,
        nome: 'Dwight',
        email: 'Dwight@gmail.com',
        idade: 39
    },
    {
        id:3,
        nome: 'Pam',
        email: 'Pam@gmail.com',
        idade: 33
    },
  ]
  }
},

  components: {
    Cliente,
    //Produto
  },
  methods: {
    adicionarCliente(){
      if(this.nomeField == "" || this.emailField == "" || this.idadeField == 0){
        alert("Preencha todos os campos!")
        return
      }
      this.clientes.push({
        nome: this.nomeField,
        email: this.emailField,
        idade: this.idadeField,
        id: Date.now()
      })
    }
  },
  computed: {
    clientesOrdenados(){
      return _.orderBy(this.clientes, ['nome'], ['asc'])
    }
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
