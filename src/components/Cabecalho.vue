<script setup>
    const props = defineProps(['tarefasPendentes']);
    // const props = defineProps([tarefasPendentes]);
</script>
<template>
    <header class="bg-light rounded-3 p-5 mb-4 mt-4">
        <h1>Minhas Tarefas</h1>
        <p v-if ="props.tarefasPendentes > 0">
            Voçe Possui {{ props.tarefasPendentes }} tarefas Pendentes
        </p>
        <p v-else ="props.tarefasPendentes = 0">
            Parabens Voçe Concluiu Todas as tarefas!
        </p>
    </header>
</template>
