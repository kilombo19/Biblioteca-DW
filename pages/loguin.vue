<template>
    <v-container fill-height style="border: 1px solid #d92525; background: #d92525">

        <v-row justify="center">
  <v-col cols="10">
    <v-card>
      <v-card-title style="align-content: center">
        <h1 >BIBLIOTECA VIRTUAL- ENSEÑA A UN BURRO</h1>
      </v-card-title>
    </v-card>  
  </v-col>
</v-row>

      <v-row justify="center">
        <v-col cols="4">
          <v-card>
            <v-card-title>
              <h1>{{ title }}</h1>
            </v-card-title>
            <v-card-subtitle>
              <span v-html="subtitle"></span>
            </v-card-subtitle>
            <v-card-text>
              <v-form v-model="formAccount" ref="formAccount">
                <v-row>
                  <v-col>
                    <v-text-field label="Correo" type="email" :rules="[rules.required, ...emailRules]"
                      v-model="account.email" required></v-text-field>
                  </v-col>
                </v-row>
                <v-row>
                  <v-col>
                    <v-text-field label="Contraseña" v-model="account.pass" :rules="[rules.required, ...passwordRules]"
                      :type="showPassword ? 'text' : 'password'" required
                      :append-icon="showPassword ? 'mdi-eye-off' : 'mdi-eye'"
                      @click:append="changeVisibilityPassword()"></v-text-field>
                  </v-col>
                </v-row>
                <v-row justify="center">
                  <v-col cols="12">
                    <v-btn color="#d92525" dark  class="text-none" @click="loginAccount">Iniciar Sesión</v-btn>
                    <v-btn color="secondary" class="text-none" nuxt to="/register"> Crear una cuenta </v-btn>
                  </v-col>
                </v-row>
                <v-row justify="center">
                  <v-col cols="12">
                    {{ message }}
                  </v-col>
                </v-row>
              </v-form>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </template>
  <script lang="ts">
  import { Account } from '~/assets/models/Account';
  export default {
    layout: 'blank',
    data() {
      return {
        message: "",
        accounts: [],
        showPassword: false,
        formAccount: null,
        title: 'Inicia Sesión',
        subtitle: 'Inicia sesión con tu cuenta creada',
        item:
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/',
        },
        account: {
          email: '',
          pass: '',
          polity: false,
        },
        // Reglas generales
        rules: {
          required: (v: String | null) => !!v || 'Este campo es obligatorio.',
        },
        //Reglas especificas
        emailRules: [(v: string) => /.+@.+\..+/.test(v) || 'El correo debe ser valido'],
        passwordRules: [
          (v: string) =>
            /^(?=\w*\d)(?=\w*[A-Z])(?=\w*[a-z])\S{8,16}$/.test(v) ||
            'Debe tener may, min, 8-16',
        ],
      }
    },

    methods: {
  changeVisibilityPassword() {
    this.showPassword = !this.showPassword;
    console.log(this.showPassword)
  },

  
},
}
  </script>
         