<template>
  <div class="box">
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
        />
      </div>

      <div class="column">
        <ChronometerControls />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import ChronometerControls from './ChronometerControls.vue'
export default defineComponent({
  name: "FormFields",
  components: {
    ChronometerControls
  },
  
});
</script>