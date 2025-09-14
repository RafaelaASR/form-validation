<script setup>  
  import { defineProps, defineEmits } from 'vue';
  const props = defineProps({
    alterar: {
      type: Boolean
    }
  });
  const emit = defineEmits(['update:alterar']);

  const toggleCadastro = () => {
    emit('update:alterar', !props.alterar);
    console.log("foi")
  }

</script>
<template>
    <div class="w-66 cadastro text-center pa-16" variant="tonal">
        <p class="text-h4 w-100 mt-16 mb-5">Cadastra</p>
        <p class="">Ainda não é cadastrdo?</p>
        <p class="font-weight-bold">Registre-se agora!</p>
        <VBtn class="mt-16 mb-16" @click="toggleCadastro">CADASTRE-SE</VBtn>
    </div>
</template>
<style>
  .cadastro{
    background-color: #fa6600;
    color: #ffffff;
  }
</style>