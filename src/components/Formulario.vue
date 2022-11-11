<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form">
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você quer iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <TemporizadorSection @aoTemporizadorFinalizado="finalizarTarefa" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TemporizadorSection from "./Temporizador.vue";

export default defineComponent({
  name: "FormularioTarefa",
  components: {
    TemporizadorSection,
  },
  data() {
    return {
      descricao: "",
    };
  },
  methods: {
    finalizarTarefa(tempoDecorrido: number): void {
      console.log(tempoDecorrido);
      console.log(this.descricao);
      this.descricao = "";
    },
  },
});
</script>

    Temporizador
<style scoped>
</style>