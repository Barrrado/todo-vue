<script setup>
import {reactive} from 'vue'

const estado = reactive({
  filtro : 'Todas',
  tarefaTemp: '',
  tarefas:[
    {
    titulo: 'Estudar ES6',
    concluido: false,
    },
    {
      titulo: 'Estudar Vue',
      concluido: false,
    },
    {
      titulo: 'Estudar React',
      concluido: false,
    },
    {
      titulo: 'Estudar Angular',
      concluido: true,
    }
]
     })
const getTarefasPendentes = () => {
  return estado.tarefas.filter(tarefa => !tarefa.concluido)
}
const getTarefasFiltradas = () => {
  const {filtro} = estado;
  switch (filtro) {
    case 'pendentes':
      return getTarefasPendentes();
    case 'concluidas':
      return estado.tarefas.filter(tarefa => tarefa.concluido);
    default:
      return estado.tarefas;
  }
}
const CadastraTarefa = () => {
  const TarefaNova = { titulo: estado.tarefaTemp , concluido: false}
  estado.tarefas.push(TarefaNova);
  estado.tarefaTemp = '';
}

</script>

<template>
<div class="container">
<header class="bg-light rounded-3 p-5 mb-4 mt-4">
  <h1>Minhas Tarefas</h1>
  <p >
    Vocçe Possui {{ getTarefasPendentes().length  }} tarefas Pendentes
  </p>
</header>
<form action="" @submit.prevent="CadastraTarefa" >
  <div class="row">
    <div class="col-md-2 ">
      <input :value="estado.tarefaTemp" @change="evento => estado.tarefaTemp = evento.target.value"  class="form-control" required type="text" placeholder="Coloque aqui a Tarefa">
    </div>
    <div class="col-md-1 p-2">
      <button class="btn btn-primary" type="submit">Adicionar</button>
    </div>
    <div class="col-md-2">
      <select  @change="evento => estado.filtro = evento.target.value" class="form-control" name="" id="">
        <option value="Todas">Todas</option>
        <option value="concluidas">Finalizado</option>
        <option value="pendente">Pendente</option>
      </select>
    </div>
  </div>
</form>
<ul class="list-group mt-4">
 <li class="list-group-item" v-for="tarefa in getTarefasFiltradas()">
 <input @change="evento => tarefa.concluido = evento.target.checked" :checked="tarefa.concluido" :id="tarefa.titulo" type="checkbox">
 <label class="ms-3" for="">
  {{tarefa.titulo}}
 </label>
</li>
</ul>
</div>
</template>

<style scoped>

</style>
