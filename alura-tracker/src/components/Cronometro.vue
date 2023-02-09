        <template>
                    <section>
                        <strong>
                            {{  tempoDecorrido }}
                        </strong>
                    </section>
            </template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        // eslint-disable-next-line vue/multi-word-component-names
        name: 'Cronometro',
        props: {
            // corresponde a tudo o que vamos receber do componente pai 
            tempoEmSegundos: {
                type: Number,
                // por padrão 
                default: 0
            }
        },
        computed: {
            tempoDecorrido(): string {
                // precisamos pegar nosso tempo em segundos do nosso componente pai 
                return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11,8)
            }
        }
    })
</script>