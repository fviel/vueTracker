<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <!-- > menu lateral<!-->
      <SideBarMenu/>
    </div>
    <div class="column is-three-quarter">
      <!-- > body da tela<!-->
      <FormFields @whenSavingATask="persistTask"/>
      <div class="listaTarefas">
          <TrackedTask v-for="(task, index) in tasks" :key="index" :task="task"  />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue"
import SideBarMenu from './components/SideBarMenu.vue'
import FormFields from './components/FormFields.vue'
import TrackedTask from './components/TrackedTask.vue'
import ITask from './interfaces/ITask'

export default defineComponent({
  name: "App",
  components:{
    SideBarMenu,
    FormFields,
    TrackedTask
  },
  data(){    
    return {
      tasks:[] as ITask []
    }
  },
  methods:{
    persistTask(task: ITask){
      console.log('Duracao da task:', task.durationInSeconds)
      console.log('Descricao da task:', task.description)
      this.tasks.push(task);
    }
  }
});
</script>

<style>
.listaTarefas{
  padding: 1.25rem;  
}
</style>
