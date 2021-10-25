<template>
<v-app>
<v-main>
  <v-container>
    <v-row align="center " justify="center">
      <v-col cols="12" sm="10">
        <v-card class="elavation-6 mt-10">
          <v-window v-model="step">
            <v-window-item :value="1">
              <v-row>
                <v-col cols="12" sm="6">
                <v-form @submit.prevent="submitHandler" ref="form">
                  <v-card-text class="mt-12">
                    <h4 class="text-center">Login into your account</h4>
                    <h6 class="text-center grey--text">Login into your account  <i class="fa fa-low-vision" aria-hidden="true"></i></h6>
            
                    <v-row align="center" justify="center">
                      <v-col cols="12" sm="8">
                      
                        <v-row>
             
                          <v-row>
                          <v-col cols="12" sm="6">
                          <v-text-field label="First Name" v-model="fname" outlined dense color="blue" autocomplete="false" class="mt-4"></v-text-field>
                          </v-col>
                          <v-col cols="12" sm="6">
                          <v-text-field label="Last Name" v-model="lname" outlined dense color="blue" autocomplete="false" class="mt-4"></v-text-field>
                          </v-col>
                        </v-row>
                         <v-text-field label="Email" outlined dense color="blue" autocomplete="false" class="mt-4" type="email" 
                         v-model="email"  :rules="emailRules"  prepend-inner-icon="mdi-account" required
                         ></v-text-field>
                         <v-text-field v-model="password" :rules="passwordRules" label="Password" outlined dense color="blue" autocomplete="false" class="mt-4" type="password"
                         prepend-inner-icon="mdi-lock" :append-icon="passwordShow ? 'mdi-eye':'mdi-eye-off'" @click:append="passwordShow = !passwordShow" required
                         
                         ></v-text-field>
                        
                          <v-text-field label=" Confirm Password" outlined dense color="blue" autocomplete="false" class="mt-4" type="password"   v-model="confirmPassword"
                            name="confirmPassword" prepend-inner-icon="mdi-lock" :append-icon="passwordShow ? 'mdi-eye':'mdi-eye-off'" @click:append="passwordShow = !passwordShow" required></v-text-field>
                                <v-col cols="12" sm="7">
                            <v-checkbox label="Remember me" class="mt-n1" ></v-checkbox>
                              </v-col>
                          <v-row></v-row> 
                        </v-row>
                        <v-btn color="blue" dark block title type="submit" :loading="loading" >Login in </v-btn>
                        <h5 class="text center grey--text mt-4 mv-3">Or login using </h5>

                        <div class="d-flex justify-space=between align-center mx-10 mb-16">
                        <v-btn depressed outlined color="grey"> <v-icon color="red">fab fa-google </v-icon></v-btn>
                        <v-btn depressed outlined color="grey"> <v-icon color="blue">fab fa-facebook -f </v-icon></v-btn>
                        <v-btn depressed outlined color="grey"> <v-icon color="light-blue lighten-3">fab fa-twitter</v-icon></v-btn>
                        </div>
                      </v-col>
                    </v-row>
                  </v-card-text>
                  </v-form>
                  
                </v-col>
                <v-col cols="12" sm="6" class="blue rounded-bl-xl">
              <div style="text-align :center; padding:180px 0;">
              <v-card-text class="white--text">
              <h3 class="text-center">Dont have an account yet?</h3>
              <h6 class="text-center">Lets get you all set up </h6>
              </v-card-text>
              </div>
                </v-col>
            </v-row>
            </v-window-item>
          
          </v-window>
        </v-card>
      
      </v-col>
    
    </v-row>
</v-container>
</v-main>
  <v-snackbar top color="green" v-model="snackbar">
      Login success
    </v-snackbar>
</v-app>
</template>

<script>

  export default {
   data: () => ({
     step:1,
    loading:false,
    snackbar:false,
    passwordShow:false,
    lname:"",
    fname:"",
    confirmPassword: '',
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
    ],
    password: '',
    passwordRules: [
      v => !!v || 'Password is required',
      v => (v && v.length >= 6) || 'Password must be 6  characters or more!',
    ],

   }),
   props:{
     source:String,
   },

    components: {
     
    },
    methods:{
    submitHandler(){
      if (this.$refs.form.validate()){
          this.loading = true
        setTimeout(()=> {
          this.loading = false
          this.snackbar = true
        },3000)
      }
    }
  }
  }
</script>
<style scoped>
.v-application .rounded-bl-xl{
  border-bottom-left-radius: 300px !important;
}
.v-application .rounded-br-xl{
  border-bottom-right-radius: 300px !important;
}
</style>