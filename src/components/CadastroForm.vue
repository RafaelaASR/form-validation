<template>
  <VRow>
    <VCol cols="6" class="ma-0 pa-0">
      <div class="form w-50 pa-10 pt-25 text-center">
        <p class="text-h4 mt-10 mb-13">Cadastrar</p>
        <form  @submit.prevent="onSubmit">
          <v-text-field
            type="text"
            label="Nome"
            v-model="nome"
            :error="nomeError"
          >
          </v-text-field>
          <v-text-field
            type="email"
            label="Email"
            v-model="email"
            :error="emailError"
          >
          </v-text-field>
          <v-text-field
            label="Password"
            type="password"
            v-model="password"
            :error="passwordError"
          >
          </v-text-field>
          <v-btn
            type="submit"
            class="-fill-gradient mt-5"
          >
            Submit
          </v-btn>
        </form>
      </div>
    </VCol>
     <VCol cols="6" class="pa-0">
        <Login :alterar="alterar" @update:alterar="$emit('update:alterar', $event)"/>
    </VCol>
  </VRow>
</template>

<script>
import { useField, useForm } from 'vee-validate';
import Login from './Login.vue';

export default {
  props: {
    alterar: Boolean
  },
  emits: [
    'update:alterar'
  ],  
  components: { Login },
  setup () {
    function onSubmit () {
      alert('Submitted')
    }

    const validations = {
      email: value => {
        if(!value) return 'This camp is required!';
  
        const regex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
          if (!regex.test(String(value).toLowerCase())) {
            return 'Please enter a valid email address'
          }
          
        return true;
      },
      passwords: value => {
        const requiredMessage = 'This fiels is required';
        if(value === undefined || value === null) return requiredMessage
        if(!String(value).length) return requiredMessage

        return true;
      },
      title: value => {
        const req = required(value)
        if(req !== true) return req

        const min = minLength(3, value)
        if(min !== true) return min

        return true;
      }
    }

    useForm({
      validationSchema: validations
    })

    const { value: nome, errorMessage: nomeError } = useField('nome')
    const { value: email, errorMessage: emailError } = useField('email')
    const { value: password, errorMessage: passwordError } = useField('password')
    
    return {
      onSubmit,
      email,
      emailError: email.errorMessage,
      password,
      passwordError,
      onSubmit
    }
  }
}
</script>
<style>
.form{
  position: relative;
  background-color: #000000b0;
  color: #ffffff;
}

</style>