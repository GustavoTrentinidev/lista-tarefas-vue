<template>
  <div class="container">
    <h2>{{ titulo }}</h2>
    <div class="input-group">
      <input type="text" v-model="novaTarefa" @keydown.enter="adicionarTarefa">
      <span class="input-group-btn">
        <button @click="adicionarTarefa" class="btn btn-primary">Adicionar Tarefa</button>
      </span>
    </div>
    <ul>
      <li v-for="(tarefa, index) in tarefas" :key="index" :class="{removed: tarefa.checked}">
        <input type="checkbox" v-model="tarefa.checked">
        <label> {{tarefa.titulo}} </label>
      </li>
    </ul>
    <footer>
      <em>Altere aqui o título da sua lista de tarefas</em>
      <input type="text" v-model="titulo">
    </footer>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return{
      titulo: "Minha Lista de Tarefas",
      novaTarefa: "",
      tarefas: [
        {titulo: "Estudar", checked: false},
        {titulo: "Programar", checked: true}
      ],
    }
  },
  methods: {
    adicionarTarefa() {
      if(this.novaTarefa !== ""){
        this.tarefas.push({
        titulo: this.novaTarefa,
        checked: false,
      });
        this.novaTarefa = "";
      }
    }
  }
}
</script>

<style>
.container{
  width: 40%;
  margin: 20px auto 0px auto;
}

ul li{
  list-style: none;
}

.removed{
  color:gray;
}
.removed label{
  text-decoration: line-through;}
</style>
