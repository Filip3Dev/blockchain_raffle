<template>
  <q-page class="flex flex-center">
    <q-card class="row q-col-gutter-lg carder">
      <div class="col-md-6 namedColors">
        <div class="">
          <h3 class="text-weight-light">
            Oxigen Lottery
          </h3>
          <img src="https://image.flaticon.com/icons/svg/1554/1554028.svg" alt="" width="120">
        </div>
      </div>
      <div class="col-md-6">
        <q-form @submit="doLogin" class="row q-col-gutter-sm full-width" v-if="isEnter">
           <q-input
             outlined
             v-model="form_login.email"
             label="Digite seu E-mail"
             class="col-md-12"
           />

           <div class="forgot">
              <p>
                Esqueceu sua senha?
              </p>
           </div>

           <q-input
            class="col-md-12"
            label="Digite sua senha"
            v-model="form_login.password"
            outlined
            :type="isPwd ? 'password' : 'text'"
           >
            <template v-slot:append>
              <q-icon
                :name="isPwd ? 'visibility_off' : 'visibility'"
                class="cursor-pointer"
                @click="isPwd = !isPwd"
              />
            </template>
          </q-input>

           <div class="col-md-12 q-mt-md">
             <div class="row full-width">
               <div class="col-md-6">
                 <q-btn label="Cadastrar" type="submit" outline @click="isEnter = false"/>
               </div>
               <div class="col-md-6" style="text-align: right;">
                 <q-btn label="Entrar" type="submit" color="accent" size="lg"/>
               </div>
             </div>
           </div>
         </q-form>
        <q-form @submit="doCadastro" class="row q-col-gutter-sm full-width" v-else>
           <q-input
             outlined
             v-model="form_cadastro.email"
             type="email"
             :rules="[val => !!val || 'O e-mail é obrigatório!']"
             label="Digite seu E-mail"
             class="col-md-12"
           />

           <q-input
             outlined
             v-model="form_cadastro.fullname"
             :rules="[val => !!val || 'Por favor digite seu nome completo!']"
             label="Digite seu nome completo"
             class="col-md-12"
           />

           <q-input
             outlined
             v-model="form_cadastro.nick"
             :rules="[val => !!val || 'Por favor digite seu apelido!']"
             label="Como gostaria de ser chamado"
             class="col-md-12"
           />

           <q-input
            class="col-md-12"
            label="Digite sua senha"
            v-model="form_cadastro.password"
            :rules="[val => !!val || 'Por favor digite sua senha!']"
            outlined
            :type="isPwd ? 'password' : 'text'"
           >
            <template v-slot:append>
              <q-icon
                :name="isPwd ? 'visibility_off' : 'visibility'"
                class="cursor-pointer"
                @click="isPwd = !isPwd"
              />
            </template>
          </q-input>

           <q-input
            class="col-md-12"
            label="Digite sua senha novamente"
            v-model="form_cadastro.password1"
            :rules="[val => !!val || 'Por favor digite sua senha novamente!']"
            outlined
            :type="isPwd1 ? 'password' : 'text'"
           >
            <template v-slot:append>
              <q-icon
                :name="isPwd1 ? 'visibility_off' : 'visibility'"
                class="cursor-pointer"
                @click="isPwd1 = !isPwd1"
              />
            </template>
          </q-input>

           <div class="col-md-12 q-mt-md">
             <div class="row full-width">
               <div class="col-md-6">
                 <q-btn label="Login" type="submit" outline @click="isEnter = true"/>
               </div>
               <div class="col-md-6" style="text-align: right;">
                 <q-btn label="Cadastrar" type="submit" color="accent"  size="lg" />
               </div>
             </div>
           </div>
         </q-form>
      </div>
    </q-card>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      isPwd: true,
      isPwd1: true,
      isEnter: true,
      form_login: {
        email: '',
        password: ''
      },
      form_cadastro: {
        email: '',
        fullname: '',
        nick: '',
        password: '',
        password1: ''
      }
    }
  },
  methods: {
    doLogin() {
      console.log(this.form_login);
      this.$router.push('home')
    },
    doCadastro() {
      console.log(this.form_cadastro);
    }
  }
}
</script>
<style lang="sass">
  .forgot
    width: 100%
    display: flex
    align-items: center
    justify-content: flex-end
    p
      margin: 16px 0px
      cursor: pointer
  .carder
    margin: 0px 100px !important
    padding: 24px
    width: 100% !important
    min-height: 50vh
  .namedColors
    background: blueviolet
    display: flex
    align-items: center
    justify-content: center
    div
      text-align: center
</style>
