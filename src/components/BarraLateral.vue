<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="Logo">
        </h1>
        <button class="button" @click="alterarTema">
            {{ textoBotao }}
        </button>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    data() {
        return {
            darkMode: false
        }
    },
    computed: {
        textoBotao() {
            if (this.darkMode) {
                return 'Dark Mode Off'
            }
            return 'Dark Mode On'
        }
    },
    methods: {
        alterarTema() {
            this.darkMode = !this.darkMode;
            this.$emit('aoTemaAlterado', this.darkMode);
        }
    }
})
</script>

<style scoped>
header {
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    padding: 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
}

header h1 {
    display: flex;
    justify-content: center;
}

@media (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>