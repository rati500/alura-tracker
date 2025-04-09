<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuro}" >
    <div class="column is-one-quarter">
      <BarraLateral @temaAlterado="trocarOtema" />
    </div>
    <div class="column is-three-quarters conteudo">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa"/>      
      <TarefaComonent v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
      <BoxPadrao v-if="listaEstaVazia">
        <p class="has-text-centered">Você não está muito produtivo hoje :(</p>
      </BoxPadrao>
    </div>
    
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioTarefa from './components/FormularioTarefa.vue';
import TarefaComonent from './components/TarefaComonent.vue';
import  ITarefa from './interfaces/ITarefa';
import BoxPadrao from './components/BoxPadrao.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioTarefa,
    TarefaComonent,
    BoxPadrao
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuro: false,
    };
  },
  computed: {
    listaEstaVazia() : boolean {
      return this.tarefas.length === 0;
    },

  },
  
  methods:{
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);    
    },
    trocarOtema(modo : boolean){
      this.modoEscuro = modo;
     
    }
  }

});
</script>

<style>

.lista{
  padding: 1.25rem;
}

main{
  --bg-primario: #FFF;
  --texto-primario: #000;
}

main.modo-escuro{
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}	

.conteudo{
  background: var(--bg-primario);
  color: var(--texto-primario);
}
</style>
