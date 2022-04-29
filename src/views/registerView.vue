<template>
  <div class="main-container">
    
      <div class="box-container">
        <h2 class="heading">Crea il tuo account</h2>
        <div class="form-fields">
          <input
            id="firstName"
            name="firstName"
            type="text"
            v-model="webSurfer.firstName"
            placeholder="Nome"
          />
          <input
            id="lastName"
            name="lastName"
            type="text"
            v-model="webSurfer.lastName"
            placeholder="Cognome"
          />
          <input
            id="email"
            name="email"
            type="text"
            v-model="webSurfer.email"
            placeholder="Email"
          />
          <input
            id="phone"
            name="phone"
            type="text"
            v-model="webSurfer.phone"
            placeholder="Telefono"
          />
        </div>
        <!-- <div class="form-fields">
          <input id="email" name="email" type="text" placeholder="Email" />
        </div>
        <div class="form-fields">
          <input id="password" name="password" type="text" placeholder="Password" />
        </div>-->
        <div class="form-fields">
          <button class="createaccount" name="commit" @click="register()">
            Crea account
          </button>
        </div>
        <div class="login-choice"><span>O registrati con</span></div>
        <SocialSignUp />
        <div>
          <p class="center">
            Accetti i nostri termini e condizioni per il trattamento dei dati
            <a href="#">Termini e condizioni</a>.
          </p>
        </div>
      </div>
   
    <div class="footer">
      <p>HAI GIA UN ACCOUNT? <a href="/"> Registrati</a></p>
    </div>
  </div>
</template>

<script>
import * as Vue from "vue";
import axios from "axios";
import App from "@/App.vue";
import VueAxios from "vue-axios";
const app = Vue.createApp(App);
app.use(VueAxios, axios);
axios.defaults.headers.common["Access-Control-Allow-Origin"] = "*";
import SocialSignUp from "../components/socialLogin.vue";
export default {
  name: "signupView",
  data() {
    return {
      webSurfer: {
        firstName: "",
        lastName: "",
        email: "",
        phone: "",
        pin: "03904800756090620171251",
        days: 7,
      },
    };
  },
  components: {
    SocialSignUp,
  },

  methods: {
    register() {
        axios.defaults.headers.common['Access-Control-Allow-Origin'] = '*';

      var url =
        "http://wifiticket.wifinetcom.net:8080/WIFITicketSystem2/TicketServlet?action=get_ticket_sms&pin=" +this.webSurfer.pin +"&nome=" +this.webSurfer.firstName +"&cognome=" +this.webSurfer.lastName +"&phone=" +this.webSurfer.phone +"&email=" +this.webSurfer.email +"&days=" +this.webSurfer.days;
      axios
        .post(url, {
        })
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        })
        .then(function () {
          // always executed
        });
    },
  },
};
</script>
