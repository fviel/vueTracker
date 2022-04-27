<template>
  <div class="box has-text-weight-bold">
    <div class="column is-7">Descrição da tarefa</div>
    <div class="column is-1">
      <ChronometerDisplay :timeAsSeconds="15" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import ChronometerDisplay from "./ChronometerDisplay.vue";

export default defineComponent({
  name: "TrackedTask",
  components: {
    ChronometerDisplay,
  },
});
</script>


<!-- estilo escopado quer dizer que somente se aplica a este componente ao para os filhos dele -->
<style scoped>
.box {
  background: #fffde8;
}
</style>

