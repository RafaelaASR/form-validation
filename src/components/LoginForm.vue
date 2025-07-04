<template>
  <form @submit.prevent="onSubmit">
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
    <v-text-field
      type="submit"
      class="-fill-gradient"
    >
    </v-text-field>
    
    <v-btn>
      Submit
    </v-btn>
  </form>
</template>

<script>
import { useField, useForm } from 'vee-validate';

export default {
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
}
</script>
<style>

</style>