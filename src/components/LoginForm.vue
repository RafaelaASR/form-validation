<template>
  <VRow>
    <VCol cols="6" class="pa-0 d-flex justify-end">
      <Cadastro :alterar="alterar" @update:alterar="$emit('update:alterar', $event)" />
    </VCol>
    <VCol cols="6" class="pa-0">
      <div class="form w-66 pa-16 text-center">
        <p class="text-h4 w-100 mt-7 mb-10">Login</p>
        <form  @submit.prevent="onSubmit">
          <v-text-field 
            class="textFieldColor"
            type="email"
            label="Email"
            v-model="email"
            :error="emailError"
            variant="underlined"
            >
            <template #prepend-inner>
              <i class="ri-mail-fill" style="font-size: 20px; color: #ffffff; margin-right: 7px;"></i>
            </template>
          </v-text-field>
          <v-text-field
            class="textFieldColor"
            label="Password"
            type="password"
            v-model="password"
            :error="passwordError"
            variant="underlined"
          >
            <template #prepend-inner>
              <i class="ri-lock-2-fill" style="font-size: 20px; color: #ffffff; margin-right: 7px;"></i>
            </template>
          </v-text-field>
          <v-btn
            type="submit"
            class="-fill-gradient mt-10" 
          >
            Submit
          </v-btn>
        </form>
      </div>
    </VCol>
  </VRow>
</template>

<script setup>
import { useField, useForm } from 'vee-validate';
import Cadastro from './Cadastro.vue';

const props = defineProps({
  alterar: {
    type: Boolean
  }
});

const emit = defineEmits([
  'update:alterar'
]);

/*export default {
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
    
    const { value: email, errorMessage: emailError } = useField('email')
    const { value: password, errorMessage: passwordError } = useField('password')
    
    return {
      onSubmit,
      email,
      emailError: email.errorMessage,
      password,
      passwordError
    }
  }
}*/
</script>
<style>
.form{
  background-color: #000000b0;
  color: #ffffff;
}
.textFieldColor{
  --v-field-border-color: #fa6600;
  --v-field-border-opacity: 1;
}

</style>