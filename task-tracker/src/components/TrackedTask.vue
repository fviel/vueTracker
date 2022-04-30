<template>
  <TaskBox>
    <div class="columns">
      <div class="column is-7">
        Descrição: {{ task.description || "Não possui descrição" }}
      </div>
      <div class="column">
        <ChronometerDisplay :timeAsSeconds="task.durationInSeconds" />
      </div>
    </div>
  </TaskBox>
</template>

<script lang="ts">
// importa o proptype para poder declarar que meu object é do tipo itask
import { defineComponent, PropType } from "vue";
import ITask from "../interfaces/ITask";
import ChronometerDisplay from "./ChronometerDisplay.vue";
import TaskBox from './TaskBox.vue'

export default defineComponent({
  name: "TrackedTask",
  components: {
    ChronometerDisplay,
    TaskBox
  },
  props: {
    task: {
      type: Object as PropType<ITask>,
      required: true,
    },
  },
});
</script>