<template>
  <div class="box formulario">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para a criação de uma nova tarefa"
      >
        <input
          type="Text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="taskDescription"
        />
      </div>

      <div class="column">
        <ChronometerControls @toStoppedChronometer="endTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import ChronometerControls from "./ChronometerControls.vue";
export default defineComponent({
  name: "FormFields",
  emits: ["whenSavingATask"],
  components: {
    ChronometerControls,
  },
  data() {
    return {
      taskDescription: "",
    };
  },
  methods: {
    endTask(timeAsSeconds: number): void {
      console.log("Tempo decorrido da tarefa: ", timeAsSeconds);
      console.log("Descrição da tarefa: ", this.taskDescription);
      this.$emit("whenSavingATask", {
        durationInSeconds: timeAsSeconds,
        description: this.taskDescription,
      });
      this.taskDescription = "";
    },
  },
});
</script>

<style>
.formulario{
  color: var(---texto-primario);
  background-color: var(--bg-primario);
}
</style>