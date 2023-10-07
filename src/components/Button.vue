<template>
    <button class="button" @click="onClick" :disabled="desabilitado">
        <span class="icone">
            <i :class="icone"></i>
        </span>
        <span>{{ descricao }}</span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent ({
    name: 'Button',
    props: {
        icone: {
            type: String,
            required: true
        },
        descricao: {
            type: String,
            required: true
        },
        desabilitado: {
            type: Boolean,
        }
    },
    emits: ['clicado'],
    methods: {
        onClick() {
            this.$emit('clicado');
        }
    }
});

</script>

<style scoped>
button {
    display: flex;
    gap: 5px;
}
</style>