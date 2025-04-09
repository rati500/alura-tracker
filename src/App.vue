<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarters">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa"/>
      
      <TarefaComonent v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
    </div>
    
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioTarefa from './components/FormularioTarefa.vue';
import TarefaComonent from './components/TarefaComonent.vue';
import  ITarefa from './interfaces/ITarefa';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioTarefa,
    TarefaComonent
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
    };
  },
  methods:{
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);    
    },
  }

});
</script>

<style></style>
