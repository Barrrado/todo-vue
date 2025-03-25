<script setup>
    const props = defineProps(['tarefaslist', 'tarefasPendenteslista']);
</script>s
<template>
    <ul class="list-group mt-4" v-if="tarefaslist.length > 0">
        <li  class="list-group-item" v-for="tarefa in props.tarefaslist">
            <input @change="evento => tarefa.concluido = evento.target.checked" :checked="tarefa.concluido"
                :id="tarefa.titulo" type="checkbox">
            <label class="ms-3" for="">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
    <h2 class="p-2" v-else=""> Nenhuma tarefa encontrada</h2>
</template>