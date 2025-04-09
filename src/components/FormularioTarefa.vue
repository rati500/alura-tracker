<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" area-label="formulário para criação de uma nova tarefa">
                <input v-model="descricao" type="text" class="input" placeholder="Qual terefa você deseja Iniciar?">
            </div>
            <div class="column">
                <TemporizadorCronometro @aoTemporizadorFinalizado="finalizarTarefa" />
            </div>
        </div>
    </div>
</template>

<script>

import TemporizadorCronometro from './TemporizadorCronometro.vue';

export default {
    name: 'FormularioTarefa',
    emits: ['aoSalvarTarefa'], 
    components: {
        TemporizadorCronometro
    },
    data(){
        return{
            descricao: '',
        }
    },
    methods: {
        finalizarTarefa(tempoEmSegundos) {
            this.$emit('aoSalvarTarefa', {
                descricao: this.descricao,
                duracaoEmSegundos: tempoEmSegundos,
            });
            this.descricao = '';             
        },
       

    },
   
};
</script>

<style>
.formulario{
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}

</style>