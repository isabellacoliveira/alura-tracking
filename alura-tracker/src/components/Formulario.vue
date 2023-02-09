<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para a criação de uma nova tarefa">
                <input 
                    type="text" 
                    class="input" 
                    placeholder="Qual tarefa você deseja iniciar?"
                    v-model="descricao">
                    <!-- linkar com o estado do componente  -->
                    <!-- o v-model vai linkar com a nossa tarefa a descrição do nosso estado -->
            </div>
            <div class="column">
                <Temporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    import Temporizador from './Temporizador.vue'; 

    export default defineComponent({
        // eslint-disable-next-line vue/multi-word-component-names
        name: 'Formulario',
        components: {
            // eslint-disable-next-line vue/no-unused-components
            Temporizador
        },
        data(){
            // metodo que retorna estado 
            return {
                descricao: ''
            }
        },
        methods: {
            finalizarTarefa(tempoDecorrido: number): void {
                console.log('tempo decorrido', tempoDecorrido)
                console.log('tarefa', this.descricao)
                this.descricao = ''
            }
        }
    })
</script>