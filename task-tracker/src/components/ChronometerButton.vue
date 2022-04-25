<template>
  <button class="button" @click="eventoClick" :disabled="isDisabled">
    <span class="icon">
      <i :class="customIcon"></i>
    </span>
    <span>{{customLabel}}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ChronometerButton",
  emits: ['clicado'],
  props: {
    isDisabled: {
      type: Boolean
    },
    customIcon: {
      type: String,
      required: true
    },
    customLabel: {
      type: String,
      required: true
    },
  },
  methods: {
    eventoClick () : void {
      console.log('clicado')
      this.$emit('clicado')      
    }
  }
});
</script>