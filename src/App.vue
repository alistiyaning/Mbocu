<template>
  <v-app>
    <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col cols="12" sm="8" md="8">
            <v-card tile elevation="-12" class="mt-10">
              <v-window v-model="step">
                <v-window-item :value="1">
                  <v-row>
                    <v-col cols="12" md="8">
                      <v-card-text class="mt-12">
                        <h1 class="text-center display-2 amber--text text--orange darken-1">Login to Mbocu</h1>
                          <v-form v-model="valid">
                              <v-card-text>
                                <v-text-field :rules="emailRules" label="Email" prepend-icon="mdi-account-circle" v-model="user.email"/>
                                <v-text-field :rules="passwordRules" label="Password" prepend-icon="mdi-lock" 
                                :type="showPassword ? 'text' : 'password' "
                                append-icon="mdi-eye-off" @click:append="handleclick" v-model="user.password"/>
                              </v-card-text>

                              <v-divider></v-divider>
                                <!-- <v-card-actions class="text-center mt-3">
                                   <v-btn rounded color="success" @click="handlesubmit" :disabled="!valid">Login</v-btn> -->
                                  <!-- <v-btn rounded color="success" >Login</v-btn>
                                </v-card-actions>  -->
                                <div class="text-center mtn5">
                                    <v-btn rounded color="success">Login</v-btn>
                                  </div>
                          </v-form>
                      </v-card-text>
                    </v-col> 
                    <v-col cols="12" md="4" class="teal amber darken-2">
                      <v-card-text class="white-text mt-12">
                        <h1 class="text-center display-1"> Hello Friend !</h1>
                        <h5 class="tect-center">Enter your personal details and start journey with us</h5>
                      </v-card-text>
                      <div class="text-center">
                        <v-btn rounded outlined="" dark @click="step++">Register</v-btn>
                      </div>
                    </v-col>     
                  </v-row>        
                </v-window-item>
                <v-window-item :value="2">
                  <v-row class="fill-height">
                    <v-col cols="12" md="4" class="teal amber darken-2">
                      <v-card-text class="white--text mt-12">
                        <h1 class="text-center display-1">Welcome Back !</h1>
                        <h5 class="text-center">To keep connected with us please login with your personal info</h5>
                      </v-card-text>
                      <div class="text-center">
                        <v-btn rounded outlined dark @click="step--">Login</v-btn>
                      </div>
                    </v-col>
                    <v-col cols="12" md="8">
                      <v-card-text class="mt-12">
                        <h1 class="text-center display-2 teal--text text--amber darken-2">Create account</h1>
                        <div class="text-center mt-4">
                          <v-from>
                            <v-card-text>
                                <v-text-field :rules="nameRules" label="Name" prepend-icon="mdi-person-circle" v-model="user.name"/>
                                <v-text-field :rules="emailRules" label="Email" prepend-icon="mdi-account-circle" v-model="user.email"/>
                                <v-text-field :rules="passwordRules" label="Password" prepend-icon="mdi-lock" 
                                :type="showPassword ? 'text' : 'password' "
                                append-icon="mdi-eye-off" @click:append="handleclick" v-model="user.password"/>
                            </v-card-text>

                            <v-divider></v-divider>
                                <!-- <v-card-actions class="text-center mt-3"> -->
                                  <!-- <v-btn rounded color="success" @click="handleRegister" :disabled="!valid">Register</v-btn> -->
                                  <div class="text-center mtn5">
                                    <v-btn rounded color="success">Register</v-btn>
                                  </div>
                                <!-- </v-card-actions> -->
                          </v-from>
                        </div>
                      </v-card-text>
                    </v-col>
                  </v-row>
                </v-window-item>
              </v-window>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      showPassword: false,
      user: {
        email: '',
        password:''
      },
      nameRules:[
        valueName => valueName !='' ||'Name is required' 
      ], 
      emailRules:[
        valueEmail => valueEmail !='' ||'Email is required' 
      ],
      passwordRules:[
        valuePassword => valuePassword !='' || 'Password is required',
        valuePassword => valuePassword.length <= 8 || 'Password maximum 8 characters'
      ],
      valid:false
    }
  },
  methods:{
    handleclick(){
      this.showPassword = !this.showPassword
    }
    // handlesubmit(){
    //   console.log(this.user)
    //   this.user={
    //     email: '',
    //     password:''
    //   }
    // }
  }
};
</script>
