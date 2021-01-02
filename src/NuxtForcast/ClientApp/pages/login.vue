<template>
  <div>
    <h1>Login</h1>
    <hr />
    <div>
      <b-form class="box" @submit.stop.prevent="onSubmit()">
        <b-form-group
          id="input-group-email"
          label="E-Mail Adresse"
          label-for="input-email"
        >
          <b-form-input
            id="input-email"
            v-model="form.email"
            :state="validation_email"
            type="email"
            required
          >
          </b-form-input>
          <b-form-invalid-feedback>
            E-Mail ist nicht gültig.
          </b-form-invalid-feedback>
        </b-form-group>

        <b-form-group
          id="input-group-password"
          label="Passwort"
          label-for="input-password"
        >
          <b-form-input
            id="input-password"
            v-model="form.password"
            :state="validation_password"
            type="password"
            required
          >
          </b-form-input>
          <b-form-invalid-feedback>
            Passwort ist ein Pflichtfeld.
          </b-form-invalid-feedback>
        </b-form-group>

        <b-button
          :disabled="!isFormValid"
          type="submit"
          class="w-25"
          variant="primary"
          >Login</b-button
        >
        |
        <b-button @click="resetForm()" variant="secondary">Reset</b-button>
      </b-form>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      form: {
        email: '',
        password: '',
      },
    }
  },
  methods: {
    isEmailValid(): boolean {
      var re = new RegExp('^(.+)@(.+){2,}\\.(.+){2,}$')
      return re.test(this.form.email)
    },
    isPasswordValid(): boolean {
      return this.form.password ? true : false
    },
    resetForm() {
      this.form.email = this.form.password = ''
    },
    onSubmit() {},
  },
  computed: {
    validation_email(): boolean {
      return this.isEmailValid()
    },
    validation_password(): boolean {
      return this.isPasswordValid()
    },
    isFormValid(): boolean {
      return this.isEmailValid() && this.isPasswordValid()
    },
  },
})
</script>
