<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <!-- > menu lateral<!-->
      <SideBarMenu/>
    </div>
    <div class="column is-three-quarter">
      <!-- > body da tela<!-->
      <FormFields/>

    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBarMenu from './components/SideBarMenu.vue';
import FormFields from './components/FormFields.vue';
export default defineComponent({
  name: "App",
  components:{
    SideBarMenu,
    FormFields
  }
});
</script>

<style>
</style>
