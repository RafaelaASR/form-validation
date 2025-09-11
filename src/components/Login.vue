<script setup>  
  import { defineProps, defineEmits } from 'vue';
  const props = defineProps({
    alterar: {
      type: Boolean
    }
  });
  const emit = defineEmits(['update:alterar']);

  const toggleLogin = () => {
    emit('update:alterar', !props.alterar)
  }

</script>
<template>
    <div class="w-50 login ma-auto text-center pa-16" variant="tonal">
      <p class="text-h4 mb-4 mt-16 mb-10">Login</p>
      <p class="">Já é cadastrado?</p>
      <p class="font-weight-bold">Entre já!</p>
      <VBtn class="mt-16 mb-16" @click="toggleLogin">LOGIN</VBtn>
    </div>
</template>
<style>
.login{
  background-color: #fa6600;
  color: #ffffff;
}
</style>