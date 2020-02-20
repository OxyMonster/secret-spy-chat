<template>
  <div class="">
        <v-btn
          color="teal accent-3 black--text"
          dark
          @click="openModal('register')"
        >
          Open Register Modal
        </v-btn>
        <v-spacer></v-spacer>

        <v-btn
          class="mt-5"
          color="teal accent-3 black--text"
          dark
          @click="openModal('login')"
        >
          Open Login Modal
        </v-btn>

        <login-register-modal v-if="isRegisterActive" 
                              :title = '"Register"'
                              :description="'123123sadasd'"
                              @onSubmit ='onSubmit($event)' />
        
        <login-register-modal v-if="isLoginActive" 
                              :title = '"Login"'
                              :description="'login loigin looogg'"
                              @onSubmit ='onSubmit($event)' />
  </div>
</template>

<script>
import LoginRegisterVue from '../components/Modal/Login-Register.vue'; 

export default {
  components: {
    
    'login-register-modal': LoginRegisterVue
  }, 

  data() {
    return {
      isRegisterActive: false, 
      isLoginActive: false, 

    }
  },

  methods: {

    openModal(modalType) {
      switch (modalType) {
        case 'register' : 
          this.isRegisterActive = true; 
          this.isLoginActive = false;  
          break;

        case 'login' : 
          this.isLoginActive = true; 
          this.isRegisterActive = false; 
          break;
      }
      this.isModalActive = true; 
    }, 

    onSubmit(e) {  
      console.log(e);
      this.$vuetify.theme.dark = true;
      this.isRegisterActive === true ? this.isRegisterActive = false : this.isLoginActive = false;  
      
    }
  }


}
</script>
