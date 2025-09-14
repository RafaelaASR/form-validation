<script setup>
  import LoginForm from './LoginForm.vue';
  import CadastroForm from './CadastroForm.vue';
  import { ref } from "vue";

  const alterar = ref(false);

</script>
<template>
  <div v-if="alterar">
    <CadastroForm class="mt-16" v-model:alterar="alterar"/>
  </div>
  <div v-else>
    <LoginForm class="mt-16" v-model:alterar="alterar"/>
  </div>
</template>