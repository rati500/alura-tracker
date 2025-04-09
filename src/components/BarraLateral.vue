<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="">
    </h1>
    <button class="button" @click="mudarOTema">
      {{ textoBtnTema }}
    </button>
  </header>
</template>

<script>

export default {
  name: 'BarraLateral',
  emits: ['temaAlterado'],
  data() {
    return {
      modoEscuro: false,
    };
  },
  computed: {
    textoBtnTema() {
      if (this.modoEscuro) {
        return 'Desativar tema escuro';
      }
      return 'Ativar tema escuro';
    },
  },
  methods: {
    mudarOTema() {
      this.modoEscuro = !this.modoEscuro;
      this.$emit('temaAlterado', this.modoEscuro);

    }
  },
};

</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
    
  }
}
</style>