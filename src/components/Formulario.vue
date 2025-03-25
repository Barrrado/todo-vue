<script setup>
    const props = defineProps(['CadastraTarefa', 'tarefaTemp', 
    'TrocarFiltro', 'editaTarefaTemp'])
</script>
<template>
<form action="" @submit.prevent="props.CadastraTarefa">
    <div class="row">
      <div class="col">
        <input :value="props.tarefaTemp" @change="props.editaTarefaTemp"  class="form-control" required type="text" placeholder="Coloque aqui a Tarefa">
      </div>
      <div class="col-md-1 mx-2">
        <button class="btn btn-primary" type="submit">Adicionar</button>
      </div>
      <div class="col-md-2">
        <select  @change="props.TrocarFiltro" class="form-control" name="" id="">
          <option value="Todas">Todas</option>
          <option value="concluidas">Finalizado</option>
          <option value="pendente">Pendente</option>
        </select>
      </div>
    </div>
  </form>
</template>


