<template>
  <q-page class="flex flex-center">
      <div class="col-md-12">
        <br>
      </div>

      <div class="col-md-12">
        <div class="cardMain">

          <!-- <div class="col-md-12">
            <q-banner inline-actions class="text-white bg-red">
              <template v-slot:avatar>
                <q-icon name="info" color="white" />
              </template>
                Seu cadastro está incompleto. Por favor complete seu cadastro.
              <template v-slot:action>
                <q-btn outline color="white" label="Cadastro" />
              </template>
            </q-banner>
          </div> -->
          <div class="col-md-6 offset-md-3">
            <q-card>
              <h4 class="q-my-md text-center">
                Vamos confirmar seus dados
              </h4>
              <q-form @submit="doSave" class="row q-col-gutter-sm full-width">
                <q-input
                  outlined
                  v-model="form_dados.fullname"
                  :rules="[val => !!val || 'Por favor digite seu nome completo!']"
                  label="Seu nome completo"
                  class="col-md-12"
                />

                <q-input
                  outlined
                  v-model="form_dados.email"
                  type="email"
                  :rules="[val => !!val || 'O e-mail é obrigatório!']"
                  label="Seu E-mail"
                  class="col-md-12"
                />

                <q-input
                  outlined
                  v-model="form_dados.birthDate"
                  :rules="[val => !!val || 'Por favor digite sua data de nascimento!']"
                  label="Sua data de nascimento"
                  class="col-md-12"
                />

                <q-input
                  outlined
                  v-model="form_dados.cpf"
                  :rules="[val => !!val || 'Por favor digite seu CPF!']"
                  label="Seu CPF"
                  class="col-md-12"
                />

                <q-input
                  outlined
                  v-model="form_dados.telefone"
                  :rules="[val => !!val || 'Por favor digite seu telefone!']"
                  label="Seu telefone"
                  class="col-md-12"
                />

                <h5 class="text-center">
                  Dados de Endereço
                </h5>

                <q-input
                  outlined
                  v-model="form_dados.city"
                  :rules="[val => !!val || 'Por favor digite sua cidade!']"
                  label="Sua cidade"
                  class="col-md-12"
                />

                <q-input
                  outlined
                  v-model="form_dados.complemento"
                  :rules="[val => !!val || 'Por favor digite seu complemento!']"
                  label="Seu complemento"
                  class="col-md-12"
                />

                <q-input
                  outlined
                  v-model="form_dados.bairro"
                  :rules="[val => !!val || 'Por favor digite seu bairro!']"
                  label="Seu bairro"
                  class="col-md-12"
                />

                <q-input
                  outlined
                  v-model="form_dados.rua"
                  :rules="[val => !!val || 'Por favor digite seu rua!']"
                  label="Sua rua"
                  class="col-md-12"
                />

                <q-input
                  outlined
                  v-model="form_dados.numero_casa"
                  :rules="[val => !!val || 'Por favor digite o numero da casa!']"
                  label="Número da sua casa"
                  class="col-md-12"
                />

                <q-input
                  outlined
                  v-model="form_dados.cep"
                  :rules="[val => !!val || 'Por favor digite o seu cep!']"
                  label="Seu CEP"
                  class="col-md-12"
                />

                <q-input
                  outlined
                  v-model="form_dados.estado"
                  :rules="[val => !!val || 'Por favor digite o seu estado!']"
                  label="Seu estado"
                  class="col-md-12"
                />

                <div class="col-md-12 q-mt-md">
                  <div class="row full-width">
                    <div class="col-md-6">

                    </div>
                    <div class="col-md-6" style="text-align: right;">
                      <q-btn label="Salvar dados" type="submit" color="accent" />
                    </div>
                  </div>
                </div>
              </q-form>
            </q-card>

          </div>
        </div>
      </div>

      <div class="col-md-12">
        <br>
      </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageValidate',
  data () {
    return {
      form_dados: {
        email: '',
        fullname: '',
        cpf: '',
        birthDate: '',
        telefone: '',
        city: '',
        complemento: '',
        bairro: '',
        rua: '',
        numero_casa: '',
        cep: '',
        estado: ''
      }
    }
  },
  created() {
    // this.$q.loading.show({
    //   delay: 400,
    //   spinnerSize: 120,
    //   message: 'Carregando...'
    // })
  },
  methods: {
    doSave() {
      console.log(this.form_cadastro);
    }
  }
}
</script>

<style lang="sass">
  .cardMain
    width: 50vw
    .q-card
      padding: 16px
      margin-bottom: 24px
      margin-top: 24px
</style>
