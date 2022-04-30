<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="Logomarca da aplicação de filas" />
    </h1>
    <button class="button" @click="changeColorTheme">
        {{getButtonLabel}}
    </button>
  </header>
</template>

<script lang="ts">
import {defineComponent} from 'vue'
export default defineComponent({
    name: 'SideBarMenu',
    emits:['toChangeTheTheme'],
    data(){
        return {
            modoEscuroAtivo: false
        }
    },
    computed:{
        getButtonLabel() : string{
            if(this.modoEscuroAtivo){
                return "Desativar modo escuro"
            }else{
                return "Ativar modo escuro"
            }
        }
    },
    methods:{
        changeColorTheme(){
            this.modoEscuroAtivo = !this.modoEscuroAtivo;
            this.$emit('toChangeTheTheme', this.modoEscuroAtivo);
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
  text-align: center;
}

@media only screen and(max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
