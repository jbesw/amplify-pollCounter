<template>
  <div id="app" class="hello">

    <h1>Welcome to the Pawnee Town Council Election</h1>
    <h4>Please follow the steps below to register your vote</h4>
    
    <h4>Please enter your email address and telephone number</h4>
    <b-form-input type="email" placeholder="Email address" v-model="email" :state="emailState" aria-describedby="input-live-feedback" />
    <b-form-invalid-feedback id="input-live-feedback">
      Email is a required field
    </b-form-invalid-feedback>
    <br>
    <b-form-input type="tel" placeholder="Telephone Number" v-model="tel" /> <br>


    <b-row align-h="center" class="mt-5">
      <b-card-group deck>
        <b-card bg-variant="primary" text-variant="white" header="Democrat" class="text-center" footer-tag="footer">
          <b-card-text>Leslie Knope (D) </b-card-text>
          <b-button size="lg" variant="success" class="btn btn-primary active"  @click="vote('Leslie', email, tel)">Vote</b-button>
        </b-card>

        <b-card bg-variant="danger" text-variant="white" header="Republican" class="text-center" footer-tag="footer">
          <b-card-text>Bobby Newport (R) </b-card-text>
          <b-button size="lg" variant="success" class="btn btn-primary active" @click="vote('Bobby', email, tel)">Vote</b-button>
        </b-card>
      </b-card-group>
    </b-row>
    <h1 ref="responseText"></h1>
  </div>  
</template>


<script>
import { API } from 'aws-amplify'
export default {
  name: 'app',
  computed: {
    emailState() {
      return this.email.length > 2 ? true : false
    }
  },
  data() {
    return {
      apiName: 'pollCounterAPI',
      voteFor: '',
      email: '',
      tel: ''
    }
  },
  methods: {
    vote: async function (voteFor, email, tel) {
      const init = {
        queryStringParameters: {
          voteFor,
          email,
          tel
        }
      }
      const response = await API.post(this.apiName, '/votes', init)
      this.$refs.responseText.innerText = email + ', thank you for voting for ' + voteFor;
      console.log(response)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
