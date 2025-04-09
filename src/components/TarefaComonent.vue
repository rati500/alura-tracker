<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao }}
            </div>
            <div class="column">
                <CronometroTask :tempoEmSegundos="tarefa.duracaoEmSegundos" />
            </div>            
        </div>
    </div>
</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import CronometroTask from './CronometroTask.vue';
import { PropType } from 'vue';
export default {
    name: 'TarefaComponente',
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true,
        }
    },
    components: {
        CronometroTask
    },



}

</script>

<style scoped>
.box {
    padding: 1.5rem;
    background: #FAF0CA;
}
</style>