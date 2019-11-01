<template>
  <q-page class="flex">
    <div class="row q-col-gutter-md full-width">
      <div class="col-md-4">
        <h5>
          Últimos sorteios
        </h5>
        <div>
          <q-list separator>

            <q-item clickable v-ripple v-for="(x, i) in lista_sorteios" :key="i">
              <q-item-section>
                <q-item-label overline>
                  Codigo do ganhador: {{x.winner}}
                </q-item-label>
                <q-item-label>
                  Ganhador: {{x.ganhador}}
                </q-item-label>
                <q-item-label caption>
                  Data do sorteio: {{x.data}}
                </q-item-label>
              </q-item-section>
            </q-item>

          </q-list>
        </div>
      </div>
      <div class="col-md-4">
        <h5>
          Sorteio em aberto
        </h5>
        <div class="ticketsList">
          <div class="mainRaffle">
            <p class="heroText">
              COD-896712
            </p>
            <p class="titleText">
              Codigo do sorteio
            </p>
          </div>
          <ul>
            <li>
              <p>
                Participantes do sorteio
              </p>
              <p>
                17
              </p>
            </li>
            <li>
              <p>
                Data do sorteio
              </p>
              <p>
                29/11/2019 - 10:00
              </p>
            </li>
          </ul>
          <div class="timer">
            <p>
              Tempo até o sorteio
            </p>
            <countdown :date="nowTimer" @updateCart="updateCart"></countdown>
          </div>
        </div>
      </div>
      <div class="col-md-4">
        <h5>
          Premiação do sorteio
        </h5>
        <div class="contentImage">
          <img src="https://www.pnglot.com/pngfile/detail/7-75758_dollar-money-png-image-background-money-bags-no.png" alt="" srcset="">
          <p>
            O premio dessa rodada é o valor arrecadado dos participantes.
          </p>
        </div>
        <div class="" style="display: none;">
          <q-form @submit="onSubmit" class="row q-col-gutter-sm full-width">
             <q-input
               outlined
               mask="#### #### #### ####"
               v-model="form.card_number"
               label="Cartão de credito"
               class="col-md-12"
             />
             <q-input
               outlined
               mask="####"
               v-model="form.cvv"
               label="CVV"
               class="col-md-4"
             />
             <q-input
               outlined
               mask="##"
               v-model="form.month"
               label="Mês"
               class="col-md-4"
             />
             <q-input
               outlined
               mask="##"
               v-model="form.year"
               label="Ano"
               class="col-md-4"
             />
             <div>
               <q-btn label="Submit" type="submit" color="primary"/>
             </div>
           </q-form>
        </div>
      </div>
      <div class="col-md-12">
        <div class="enterSection">
          <h4>
            Participe agora do sorteio
          </h4>
          <q-btn label="Participar" class="amazingButton" to="/home/validar-dados"/>
        </div>
      </div>
    </div>
    <q-page-sticky position="bottom-right" :offset="[18, 18]">
      <q-btn fab icon="help" color="black" />
      <q-tooltip>
        Ajuda
      </q-tooltip>
    </q-page-sticky>
  </q-page>
</template>

<script>
import countdown from '../../components/Countdown.vue';
require('moment/locale/pt-br');
const moment = require('moment');
const JSEncrypt = require('node-jsencrypt');
const MoipCreditCard = require('moip-sdk-js').MoipCreditCard;
import { MoipValidator } from 'moip-sdk-js';
const pubKey = `-----BEGIN PUBLIC KEY-----
                MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA9YTgXawViNRM2YPgFj6r
                S0AmZQLXDRmPXnMkYTd4S4r6b4b8LHUPQz94MH6fLMvyyITeUpF4ecggRrwWrMJr
                Xv3JFYRq0YWL91NZY0haZxKAG8el71da4+PM6D40t1o/5861jJ1koVWh6Wt7eE0l
                PfAlzYOKHuvCN8e3P094ozp+tIgjf5tVlad1K55ezHBJxEcQ0gwGJKgArJI86QcI
                ZHwqg4mMHCFdZavrpFdSxGbWT7cFSXBuoJTg9LoecZMiPuLdbJpj8vi0UkVUkjO8
                lBvorN+7xbnwq32T2k/zq/2fuz7o+Y6kXnrK7ho1w+ySs7gi0g8jV0q6u4210PVJ
                VQIDAQAB
                -----END PUBLIC KEY-----`;
export default {
  name: 'PageIndex',
  components: {
    countdown,
  },
  data () {
    return {
      form: {
        card_number: '',
        cvv: '',
        month: '',
        year: ''
      },
      lista_sorteios: [
        {
          ganhador: 'Pedro Paiva',
          hash: '0x781f1155fe3e9244865207cb1cc387',
          winner: '0x944f9806a01e80d95246c489bdb02d7c5e8e587a',
          data: 'Aug-21-2017 12:29:40 AM'
        },
        {
          ganhador: 'Cecilia Meireles',
          hash: '0x7675b37db39207a90e0299b7f7089c7',
          winner: '0xa7757ed7c0ec836515fdede7a4ced3603c40173c',
          data: 'Aug-22-2017 11:21:40 AM'
        },
        {
          ganhador: 'Rafael Gusmão',
          hash: '0x6c9d45d9a7d673ef0d6375c934e6303',
          winner: '0xf8e96a20ebfdf6daaa9d8a78b8a99f37747fb618',
          data: 'Aug-29-2017 10:19:40 AM'
        }
      ]
    }
  },
  computed: {
    nowTimer(){
      let now = new Date()
      let top = moment('11-29-2019').add(15, 'minutes')
      return top._d
    }
  },
  methods: {
    updateCart() {
      console.log(e);
    },
    onSubmit () {
      let retorno = MoipValidator.isValidNumber(this.form.card_number);
      if (retorno) {

      }
      MoipCreditCard
      .setEncrypter(JSEncrypt, 'ionic')
      .setPubKey(pubKey)
      .setCreditCard({
          number: this.form.card_number,
          cvc: this.form.cvv,
          expirationMonth: this.form.month,
          expirationYear: this.form.year
      })
      .hash()
      .then(hash => console.log('hash', hash));
    }
  }
}
</script>
<style lang="sass">
  .amazingButton
    padding: 22px 70px
    border-radius: 40px
    background: linear-gradient(90deg, rgba(7,7,217,1) 0%, rgba(0,212,255,1) 100%)
    color: white
    font-weight: 600
    font-size: 18px
  .enterSection
    display: flex
    align-items: center
    justify-content: center
    flex-direction: column
  .contentImage
    display: flex
    align-items: center
    justify-content: center
    flex-direction: column
    width: 90%
    img
      max-width: 70%
    p
      text-align: center
  .timer
    text-align: center
    >p
      font-size: 18px
      font-weight: 200
      margin: 0px
  .mainRaffle
    text-align: center
    .heroText
      font-size: 24px
      font-weight: 600
      margin: 0px
    .titleText
      font-weight: 200
      font-size: 18px
  .ticketsList
    ul
      margin: 0px
      padding: 0px
      li
        display: flex
        justify-content: space-between
        p
          &:first-of-type
            font-size: 18px
            font-weight: 200
          &:last-of-type
            font-size: 22px
            font-weight: 600
</style>
