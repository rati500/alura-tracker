<template>
<div class="is-flex is-align-items-center is-justify-content-space-between">
                    <CronometroTask :tempoEmSegundos="tempoEmSegundos" />
                    <button class="button" @click="iniciar" aria-label="Iniciar tarefa" :disabled="cronometroRodando">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>

                    <button class="button" @click="finalizar" aria-label="Finalizar tarefa" :disabled="!cronometroRodando">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>
                </div>
</template>

<script>
import CronometroTask from './CronometroTask.vue';

export default {
    name: 'TemporizadorCronometro',
    emits: ['aoTemporizadorFinalizado'],
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro : 0,
            croometroRodando: false,        
        };
    },
    components: {
        CronometroTask,
    },   
    methods: {
        iniciar() {
            this.cronometroRodando = !this.cronometroRodando;
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos++;                
            }, 1000);           
        },
        finalizar() {
            this.cronometroRodando = !this.cronometroRodando;
            clearInterval(this.cronometro);            
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0;   
        },
    },
};

</script>