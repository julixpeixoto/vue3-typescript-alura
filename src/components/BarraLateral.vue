<template>
  <header>
    <h1><img src="../assets/logo.jpg" alt="" /></h1>
    <button class="button" @click="alterarTema">{{ textoBotaoTema }}</button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "App",
  data() {
    return {
      temaEscuro: false,
    };
  },
  computed: {
    textoBotaoTema() {
      if (this.temaEscuro) {
        return "Desativar modo escuro";
      }
      return "Ativar modo escuro";
    },
  },
  emits: ["aoAlterarTema"],
  methods: {
    alterarTema() {
      this.temaEscuro = !this.temaEscuro;
      this.$emit("aoAlterarTema", this.temaEscuro);
    },
  },
});
</script>

<style scoped>
header {
  padding: 6rem;
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