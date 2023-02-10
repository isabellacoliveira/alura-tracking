<template>
    <Box>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <!-- quando colocamos 2 pontos é uma variavel  -->
                <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </Box>
</template>
<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent, PropType } from 'vue';
import Cronometro from "./Cronometro.vue";
import Box from './Box.vue';

 export default defineComponent({
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Tarefa',
    components: {
        Cronometro,
        Box
    },
    props: {
        tarefa: {
            // a tarefa que estamos recebendo é desse tipo especifico 
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
 })

</script>
