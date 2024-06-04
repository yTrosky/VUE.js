<template>
   <div :class="{'cliente': !isPremium, 'cliente-premium': isPremium}">
    <h4>Nome: {{cliente.nome}}</h4>
    <p>E-mail: {{ cliente.email }}</p>
    <p v-if="showIdade == true"> Idade: {{ cliente.idade }}</p>
    <p v-else> Idade: Não informada</p>
    <button @click="mudarCor">Mudar cor!</button>

   </div>
</template>

<script>
export default {
    data(){
        return {
            isPremium: false
        }
    },
        props: {
            cliente: Object,
            showIdade: Boolean
        },
        methods: {
            mudarCor(){
                this.isPremium = !this.isPremium;
            }
    }
}
</script>

<style scoped>
.cliente {
    background-color: #f4f4f4;
    margin: 10px;
    padding: 10px;
    border-radius: 5px;
}

.cliente-premium{
    background-color: black;
    color: white;
    border: 1px #ccc dotted;
    padding: 10px;
    border-radius: 5px;
}

</style>
