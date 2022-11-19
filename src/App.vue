<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro' : modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral @aoAlterarTema="alterarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <TarefaLista v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <Box v-if="listaEstaVazia">
          Você não está produtivo hoje! :(
        </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import FormularioTarefa from "./components/Formulario.vue";
import TarefaLista from './components/Tarefa.vue';
import Box from './components/Box.vue';
import Itarefa from './interfaces/ITarefa';

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    FormularioTarefa,
    TarefaLista,
    Box
  },
  data () {
    return {
      tarefas : [] as Itarefa[],
      modoEscuroAtivo: false
    }
  },
  computed : {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0;
    }
  },
  methods: {
    salvarTarefa (tarefa: Itarefa) {
      this.tarefas.push(tarefa);
    },
    alterarTema(modoEscuroAtivo : boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo;
    }
  }
});
</script>

<style>
.lista {
  padding: 1.2em;
}

main {
  --bg-primario: #fff;
  --text-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2d2d42;
  --text-primario: #ddd;
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
