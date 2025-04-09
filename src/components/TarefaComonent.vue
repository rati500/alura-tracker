<template>
    <BoxPadrao>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronometroTask :tempoEmSegundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </BoxPadrao>
</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import CronometroTask from './CronometroTask.vue';
import { PropType } from 'vue';
import BoxPadrao from './BoxPadrao.vue';
export default {
    name: 'TarefaComponente',
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true,
        }
    },
  
    components: {
        CronometroTask, BoxPadrao
    },



}

</script>
