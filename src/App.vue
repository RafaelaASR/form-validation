<script setup>

import fundoLogin from '@/assets/fundo-moto.webp';
import Principal from './components/Principal.vue';
const imgFundo = {
  backgroundImage: `url('${fundoLogin}')`,
  backgroundSize: 'cover',
  backgroundPosition: 'center',
  backgroundRepeat: 'no-repeat',
  height: '51vw',
  overflow: 'hidden',
};

</script>

<template>
  <div class="login" :style="imgFundo">
    <Principal />
  </div>
</template>

<style scoped>


</style>
