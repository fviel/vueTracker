<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <!-- este display do crtonometro troquei pelom componente Chronometer
         <section>
            <strong>{{runnedTime}}</strong>
         </section>-->
    <ChronometerDisplay :timeAsSeconds="timeAsSeconds" />

    <!-- <button class="button" @click="initializeCount" :disabled="cronoIsRunning">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>Play</span>
    </button> 
    
    <button class="button" @click="finalizeCount" :disabled="!cronoIsRunning">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>Stop</span>
    </button> -->
    <!-- o @click quer dizer: ao receber o evento @click, execute a função X 
    Mas a complexidade aqui é grande, pois o ChronometerButton escuta o evento 'clicado', e quando o recebe, passa o nome da função a ser aplicado no seu método click-->
    <ChronometerButton @clicado="initializeCount" customIcon="fas fa-play" customLabel="play" :isDisabled="cronoIsRunning" />
    <ChronometerButton @clicado="finalizeCount" customIcon="fas fa-stop" customLabel="stop" :isDisabled="!cronoIsRunning" />
  </div>
</template>

<script lang='ts'>
import { defineComponent } from 'vue'
import ChronometerDisplay from './ChronometerDisplay.vue'
import ChronometerButton from './ChronometerButton.vue'

export default defineComponent({
  name: 'ChronometerControls',
  emits: ['toStoppedChronometer'],
  components: {
    ChronometerDisplay,
    ChronometerButton
  },
  data (){
    return {
      timeAsSeconds:0,
      cronometer:0,
      cronoIsRunning: false
    }
  },
  
  methods: {
    initializeCount(){
      this.cronoIsRunning=true
      setInterval(() =>{
        this.cronometer = this.timeAsSeconds += 1
      },1000)
    },

    finalizeCount(){      
      this.cronoIsRunning = false
      console.log('finalizando contagem.');
      clearInterval(this.cronometer)
      this.cronometer = 0
      // emite um evento
      this.$emit('toStoppedChronometer', this.timeAsSeconds)
      this.timeAsSeconds = 0
    }
  }
})
</script>
