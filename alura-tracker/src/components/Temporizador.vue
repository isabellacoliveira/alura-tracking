<template>
    <section class="is-flex is-align-items-center is-justify-content-space-between">
      <Cronometro :tempoEmSegundos="tempoEmSegundos"/>
      <Botao @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
      <Botao @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
    </section>
  </template>
  

<script lang="ts">
    import { defineComponent } from 'vue';
    import Cronometro from './Cronometro.vue'; 
    import Botao from './Botao.vue'; 

    export default defineComponent({
        // eslint-disable-next-line vue/multi-word-component-names
        name: 'Temporizador',
        // o temporizador vai emitir uma coisa em determinado momento 
        // lista de eventos que ele é capaz de emitir ,
        emits: ['aoTemporizadorFinalizado'],
        components: {
            Cronometro,
            Botao
        },
        data(){
            return {
                tempoEmSegundos: 0,
                cronometro: 0,
                cronometroRodando: false
            }
        }, 
        computed: {
            tempoDecorrido(): string {
                return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11,8)
            }
        },
        methods: {
            iniciar() {
                this.cronometroRodando = true
                this.cronometro = setInterval(() => {
                    this.tempoEmSegundos += 1
                }, 1000)
            }, 
            finalizar(){
                this.cronometroRodando = false
                // vamos passar o id do intervalo e ele para dem executar 
                clearInterval(this.cronometro)
                // avisar para o pai que o evento foi finalizado 
                // recebe 2 parametros: nome do evento emitido e o segundo a carga de dados emitida 
                this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
                // resetar 
                this.tempoEmSegundos = 0
            }
        }
    })
</script>
