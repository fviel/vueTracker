<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivoLocal }">
    <div class="column is-one-quarter">
      <!-- > menu lateral<!-->
      <SideBarMenu @toChangeTheTheme="changeThemeColor"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <!-- > body da tela<!-->
      <FormFields @whenSavingATask="persistTask" />
      <div class="listaTarefas">
        <TrackedTask v-for="(task, index) in tasks" :key="index" :task="task" />
        <TaskBox v-if="taskListisEmpty"> Nenhuma tarefa inicializada. </TaskBox>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBarMenu from "./components/SideBarMenu.vue";
import FormFields from "./components/FormFields.vue";
import TrackedTask from "./components/TrackedTask.vue";
import ITask from "./interfaces/ITask";
import TaskBox from "./components/TaskBox.vue";

export default defineComponent({
  name: "App",
  components: {
    SideBarMenu,
    FormFields,
    TrackedTask,
    TaskBox,
  },
  data() {
    return {
      tasks: [] as ITask[],
      modoEscuroAtivoLocal: false
    };
  },
  computed:{
    taskListisEmpty() : boolean{
      return this.tasks.length === 0
    }
  },
    methods: {
    persistTask(task: ITask) {
      // console.log('persistTask - Duracao da task:', task.durationInSeconds)
      // console.log('persistTask - Descricao da task:', task.description)
      this.tasks.push(task);
    },
    changeThemeColor(modoEscuroAtivo: boolean){
      
      this.modoEscuroAtivoLocal = modoEscuroAtivo
      console.log('modoEscuroAtivoLocal: ', this.modoEscuroAtivoLocal)
    }
  },
});
</script>

<style>
.listaTarefas {
  padding: 1.25rem;
}

main{
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro{
  --bg-primario: rgb(4, 1, 44);
  --texto-primario: #fff;
}
.conteudo{
  background-color: var(--bg-primario);
}
</style>
