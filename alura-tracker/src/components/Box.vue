<template>
    <div class="box has-text-weight-bold" :style="estilos">
        <!-- é equivalente ao ng-template -->
        <slot></slot>
    </div>
</template>
<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        // eslint-disable-next-line vue/multi-word-component-names
        name: 'Box',
        data(){
            return {
                estilos: {
                    background: '#FAF0CA'
                }
            }
        }
    })
</script>
