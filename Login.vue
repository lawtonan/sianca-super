<template >
    <div class="login">
        <h2>Sign In</h2>
          <v-layout>
    <v-flex xs12 sm8 offset-sm5>
        <v-layout align-center>
        <v-flex xs4 >
          <v-text-field
            full-width="false"
            v-model="email"
            label="Email"
            single-line
            solo
          ></v-text-field>
          <v-text-field
            v-model="password"
            label="Password"
            single-line
            solo
          ></v-text-field>
      </v-flex >
      </v-layout>
      </v-flex >
      </v-layout>
        <v-btn @click="login">Connection</v-btn>
       <p>Don't have an account? Create one <router-link to="/sign-up">here</router-link></p>
    </div>
</template>

<script>
import firebase from 'firebase';

    export default {
        name: 'login',
        data(){
            return{
                email: '',
                password: ''
            }
        },
        methods: {
            login: function(){
                firebase.auth().signInWithEmailAndPassword(this.email, this.password).then(
                    () => {
                        this.$router.replace('home')
                    },
                    function(err){
                        alert(err)
                    }
                );
               
            }
        }
    }
</script>

<style scoped>
    
    h2{
        padding:15px;
    }
    .login {
        
        margin-top: 40px;
    }
    input {
        margin: 10px 0;
        width: 20%;
        padding: 15px;
    }
    p {
        margin-top: 40px;
        font-size: 13px;
    }
    p a {
        text-deoration: underline;
        cursor: pointer;
    }
</style>