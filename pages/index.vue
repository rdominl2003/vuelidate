<template>
<div>
  <div>
    <label>Field:</label>
    <input v-model="state.firstName">
    <div v-if="v$.firstName?.$error">firstName field has an error.</div>
  </div>
  State: 
  <br>
  <pre>
    {{state}}
  </pre>
  Vuelidate:
  <br>
  <pre>
    {{v$}}
  </pre>
</div>
</template>

<script>
import { reactive } from 'vue' // "from '@vue/composition-api'" if you are using Vue 2.x
import useVuelidate from '@vuelidate/core'
import { required } from '@vuelidate/validators'

export default {
  setup () {
    const state = reactive({
      firstName: ''
    })
    const rules = {
      firstName: { required }, // Matches state.firstName
    }

    const v$ = useVuelidate(rules, state)

    return { state, v$ }
  }
}
</script>
</script>
