<template>
    <BoxArea>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronometroTempo :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxArea>
</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent, PropType } from 'vue';
import CronometroTempo from './Cronometro.vue';
import BoxArea from './Box.vue';

export default defineComponent({
    name: 'ListaTarefa',
    components: {
        CronometroTempo, 
        BoxArea
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})

</script>

<style scoped>

</style>