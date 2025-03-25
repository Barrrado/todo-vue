<script setup>

import {reactive} from 'vue';
import Cabecalho from "./components/Cabecalho.vue";
import Formulario from "./components/Formulario.vue";
import Listagem from "./components/Lista.vue";

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
    case 'pendente':
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
  <Cabecalho :tarefasPendentes="getTarefasPendentes().length" />
<Formulario :TrocarFiltro="evento => estado.filtro = evento.target.value" :tarefaTemp ="estado.tarefaTemp"  :editaTarefaTemp="evento => estado.tarefaTemp = evento.target.value" :CadastraTarefa="CadastraTarefa"/>
<Listagem  :tarefaslist="getTarefasFiltradas()" :tarefasPendenteslista="getTarefasPendentes()"  />
</div>
</template>

<style scoped>

</style>
