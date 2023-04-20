<template>
    <header>
        <h1>
            <img alt="Tracker" src="../assets/logo.png">

        </h1>
        <div class="has-text-centered">
            <button class="button" @click="alterarModo"> {{ textoBtn }} </button>
        </div>
        <nav class="panel mt5">
            <ul>
                <li>
                    <router-link to="/" class="link">
                        <i class="fas fa-tasks"></i>
                        tarefas
                    </router-link>
                </li>
                <li>
                    <router-link to="/projetos" class="link">
                        <i class="fas fa-project-diagram"></i>
                        projetos
                    </router-link>
                </li>
            </ul>
        </nav>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BarraLateral',
    emits: ['aoAlterarModo'],
    data() {
        return {
            modoEscuro: false
        }
    },
    computed: {
        textoBtn() {
            if (this.modoEscuro) {
                return 'Desativar modo escuro'
            }

            return 'Ativar modo escuro'
        }
    },
    methods: {
        alterarModo() {
            this.modoEscuro = !this.modoEscuro
            this.$emit('aoAlterarModo', this.modoEscuro)
        }
    }
})
</script>

<style scoped>
/* todo o estilo do componente */
header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;
}

@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
.panel li {
    margin: 8px 0;
}
.link {
    color: #fff;
}
.link:hover {
    color: #FAF0CA;
}
.link.router-link-active {
    color: #FAF0CA;
}
</style>