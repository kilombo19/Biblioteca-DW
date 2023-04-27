<template>
  <v-container fill-height style="border: 1px solid #d92525; background: #d92525">
    <v-row justify="center">
      <v-col cols="10">
        <v-card>
          <v-card-title style="align-content: center">
            <h1 >BIBLIOTECA VIRTUAL - ENSEÑA A UN BURRO</h1>
          </v-card-title>
        </v-card>  
      </v-col>

    </v-row>
    <v-row justify="center">
      <v-col cols="10">
        <v-card>
          <v-card-title>
            <h1>{{title}}</h1>
          </v-card-title>
          <v-card-subtitle>
            <span v-html="subtitle"></span>
          </v-card-subtitle>
          <v-card-text>
            <v-form>
              <v-row>
                <v-col>
                  <v-text-field label="Nombres" v-model="account.firstname" :rules="[rules.required, ...nameRules]" required counter="20"> </v-text-field>
                </v-col>
                <v-col>
                  <v-text-field label="Apellidos" v-model="account.lastname" :rules="[rules.required, ...nameRules]" required counter="20"> </v-text-field>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <v-text-field label="Correo" type="email" v-model="account.email" :rules="[rules.required, ...emailRules]"> </v-text-field>
                </v-col>
                <v-col>
                  <v-text-field label="Contraseña" v-model="account.pass" :rules="[rules.required, ...passwordRules]"
                   :type="showPassword ? 'text' : 'password'" required
                   :append-icon="showPassword?'mdi-eye-off' : 'mdi-eye'"
                   @click:append="changeVisibilityPassword()">
                  </v-text-field>
                </v-col>
              </v-row>

              <v-row justify="start">
                <v-col cols="6">
                  <v-checkbox label="Aceptar Terminos y Condicionaes" v-model="account.polity" required :rules="[rules.required]"> </v-checkbox>
                </v-col>
              </v-row>
              <v-row justify="space-between">
                <v-col cols="3">
                  <v-btn color="#d92525" dark class="text-none" @click="createAccount"> Crear Cuenta</v-btn>
                </v-col>
                <v-col>
                  <v-btn color="secondary" class="text-none" to="/loguin">Cancelar</v-btn>
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
export default {
  layout: 'blank',
  data() {
   return {
    showPassword: false,
    formAccount: null,
    title: 'Crear cuenta',
    subtitle: 'Crea tu cuenta para poder reservar libros',
    account: {
      firstname: '',
      lastname: '',
      email: '',
      pass: '',
      polity: false,
    },
    // Reglas generales
    rules: {
      required: (v: String | null) => !!v || 'Este campo es obligatorio.',
    },
    // Reglas especificas
    nameRules: [
      (v: String | null) =>
        (v && v.length <= 20) ||
        'El nombre debe contener máximo 20 caracteres ',
    ],
    emailRules: [(v: string) => /.+@.+\..+/.test(v) || 'El correo debe ser valido'],
    passwordRules: [
      (v: string) =>
        /^(?=\w*\d)(?=\w*[A-Z])(?=\w*[a-z])\S{8,16}$/.test(v) ||
        'Debe tener may, min, 8-16',
    ],
  }
},

methods:{
  changeVisibilityPassword(){
    this.showPassword = !this.showPassword;
    console.log(this.showPassword)
  },

  createAccount(){
     // Acceder al formulario por medio del atributo ref
     const refFormAccount: any = this.$refs['formAccount']
     //   Activar la validacion de campos
     if (refFormAccount) {
       const formIsValid = refFormAccount.validate()
       if (formIsValid) {
         console.log('formIsValid', formIsValid)
         const url = "http://localhost:3000/accounts"
         this.$axios.post(url, account).then((response) => {
         console.log("Cuenta creada correctamente", response)
         }).catch((error) => {
          console.log("Ha ocurrido un error", error)
         }).finally(() => {
           console.log("Ha finalizado la creación de cuenta");
         })
       } else {
         alert('Formulario no valido')  
       }
     }
  },
  },
}
</script>