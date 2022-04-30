<template>
  <div class="box has-text-weight-bold">
    <!-- o slot faz com que o conteúdo do outro componente seja renderizado dentro dele -->
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent} from "vue";
export default defineComponent({
  name: "TaskBox",   
});
</script>


<!-- estilo escopado quer dizer que somente se aplica a este componente ao para os filhos dele -->
<style scoped>
.box {
  background: #b8d8eb;
}
</style>
