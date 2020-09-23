<template>
  <div id="app" class="hello">

    <h1>Welcome to the Pawnee Town Council Election</h1>
    <h4>Please follow the steps below to register your vote</h4>
    
    <h4>Please enter your email address and telephone number</h4>
    <b-form-input type="email" placeholder="Email address" v-model="email" /> <br>
    <b-form-input type="tel" placeholder="Telephone Number" v-model="tel" /> <br>

    <b-row align-h="center" class="mt-5">
      <b-card-group deck>
        <b-card bg-variant="success" text-variant="white" header="Vote Leslie Knope" class="text-center" footer-tag="footer">
          <b-card-text>Leslie Knope</b-card-text>
          <b-button size="lg" variant="primary"  @click="vote('Leslie', email, tel)">Button</b-button>
        </b-card>

        <b-card bg-variant="danger" text-variant="white" header="Vote Bobby Newport" class="text-center" footer-tag="footer">
          <b-card-text>Bobby Newport</b-card-text>
          <b-button size="lg" variant="primary" @click="vote('Bobby', email, tel)">Button</b-button>
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
  data() {
    return {
      apiName: 'pollCounterAPI',
      vote: '',
      email: '',
      tel: ''
    }
  },
  methods: {
    vote: async function (vote, email, tel) {
      const init = {
        queryStringParameters: {
          vote,
          email,
          tel
        }
      }
      const response = await API.post(this.apiName, '/votes', init)
      this.$refs.responseText.innerText = email + ', thank you for voting for ' + vote;
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
