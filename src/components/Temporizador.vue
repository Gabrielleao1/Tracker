<template>
    <Cronometro :tempo-em-segundos="tempoEmSegundos" />

    <Button @clicado="iniciar" icone="fas fa-play" descricao="Play" :desabilitado="cronometroRodando" />

    <Button @clicado="finalizar" icone="fas fa-stop" descricao="Stop" :desabilitado="!cronometroRodando" />
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import Cronometro from './Cronometro.vue';
import Button from './Button.vue';

export default defineComponent({
    name: 'Temporizador',
    emits: ['aoTemporizadorFinalizado'],
    components: {
    Cronometro,
    Button
},
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
    methods: {
        iniciar() {
            this.cronometroRodando = true;
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1;
            }, 1000);
        },
        finalizar() {
            this.cronometroRodando = false;
            clearInterval(this.cronometro);
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0
        }
    }
})
</script>

<script scoped>
</script>