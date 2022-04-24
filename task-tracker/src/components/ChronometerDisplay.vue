<!-- Componente de exibição do contador do cronômetro -->
<template>
  <section>
    <strong>{{ runnedTime }}</strong>
  </section>
</template>

<script lang='ts'>
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'ChronometerDisplay',
    props: {
        timeAsSeconds:{
            type: Number,
            default: 0
        }
    },
    computed:{
    runnedTime() : string {
      return  new Date(this.timeAsSeconds * 1000).toISOString().substr(11,8);
    }
  },
})
</script>
