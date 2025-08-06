<template>
    <div>
        <h2>Lista de tarefas</h2>
        <v-card>
            <v-list>
                <v-list-item
                v-for="tarefa in tarefas"
                :key="tarefa.id"
                >
                    <v-list-item-content>
                        <v-list-item-title>{{ tarefa.title }}</v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
            </v-list>
        </v-card>
    </div>

</template>
<script setup>
import { ref, onMounted} from 'vue';
const tarefas = ref([])

onMounted(async() => {
    try {
        const resposta = await fetch('https://jsonplaceholder.typicode.com/todos');
        const dados = await resposta.json();
        tarefas.value = dados;
    } catch (erro) {
        console.log('Erro ao carregar tarefas', erro)
    }
    return {tarefas};
});
</script>