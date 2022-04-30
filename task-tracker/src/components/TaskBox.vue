<template>
  <div class="box has-text-weight-bold" :style="estilos">
    <!-- o slot faz com que o conteúdo do outro componente seja renderizado dentro dele -->
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent} from "vue";
export default defineComponent({
  name: "TaskBox",  
  data(){
    return{
      estilos:{
        backgroundColor:  '#b8d8eb'
        //background-color: '#b8d8eb'
      }
    }
  } 
});
</script>


<!-- estilo escopado quer dizer que somente se aplica a este componente ao para os filhos dele 
Este aqui é o jeito mais comum de passar o estipo, mas usando o comando :stype, 
posso passar ele dentro de script, o que permite maior flexibilidade de programação
<style scoped>
.box {
  background: #b8d8eb;
}
</style>
-->