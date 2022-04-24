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
        <div
          class="is-flex is-align-items-center is-justify-content-space-between"
        >
          <section>
            <strong>{{runnedTime}}</strong>
          </section>

          <button class="button" @click="initializeCount">
            <span class="icon">
              <i class="fas fa-play"></i>
            </span>
            <span>Play</span>
          </button>

          <button class="button" @click="finalizeCount">
            <span class="icon">
              <i class="fas fa-stop"></i>
            </span>
            <span>Stop</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "FormFields",
  data (){
    return {
      timeAsSeconds:0,
      cronometer:0
    }
  },
  computed:{
    runnedTime() : string {
      return  new Date(this.timeAsSeconds * 1000).toISOString().substr(11,8);
    }
  },
  methods: {
    initializeCount(){
      setInterval(() =>{
        this.cronometer = this.timeAsSeconds += 1
        //console.log('Incrementando o contador');
      },1000)
      //console.log('iniciando contagem.');
    },
    finalizeCount(){
      //console.log('finalizando contagem.');
      clearInterval(this.cronometer)
    }
  }
});
</script>