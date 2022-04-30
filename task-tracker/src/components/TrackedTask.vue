<template>
  <div class="box has-text-weight-bold">
    <div class="column is-7">Descrição: {{task.description}} </div>
    <div class="column">
      <ChronometerDisplay :timeAsSeconds="task.durationInSeconds" />
    </div>
  </div>
</template>

<script lang="ts">
// importa o proptype para poder declarar que meu object é do tipo itask
import { defineComponent, PropType } from "vue";
import ITask from "../interfaces/ITask";
import ChronometerDisplay from "./ChronometerDisplay.vue";

export default defineComponent({
  name: "TrackedTask",
  components: {
    ChronometerDisplay,
  },
  props:{
      task:{
          type: Object as PropType<ITask>,
          required: true
      }
  }
});
</script>


<!-- estilo escopado quer dizer que somente se aplica a este componente ao para os filhos dele -->
<style scoped>
.box {
  background: #fffde8;
}
</style>

