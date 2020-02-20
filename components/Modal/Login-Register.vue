<template>
 <div class="text-center">
    <v-dialog 
      v-model="dialog"
      width="700"
     
    >
 

      <v-card class="pb-4">
        <v-card-title
          class="headline teal accent-3 black--text lighten-2"
          primary-title
        >
          {{ title }}
        </v-card-title>

        <v-card-text class="mt-4 justify-center d-flex">
          <h4>
           {{ description }}
          </h4> 
            
        </v-card-text>

        <v-divider></v-divider>
    <v-container grid-list-md>
          <v-text-field class="mt-3"
            label="Username"
            outlined
            color="teal accent-3"
            v-model="userData.userName"
          ></v-text-field>
    
          <v-text-field
            label="Password"
            outlined
            color="teal accent-3"
            type="password"
            v-model="userData.password"
          ></v-text-field>
      
    </v-container>
        
    

        <v-card-actions class="justify-center">
     
          <v-btn
            color="teal accent-3 black--text"
            dark
            @click="closeModal"
          >
            <p class="my-0" v-if="title === 'Register'">Register</p> 
            <p v-else class="my-0"> Login </p>
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
    name: "Login-Register-Modal", 
    props: [
      'title',
      'description',
    ], 

    data() {
      return {
        dialog: true,
        userData: {
          userName: '', 
          password: ''
        }
      }
    },
    methods: {
      closeModal() {
        
        this.$emit('onSubmit', this.userData); 
      }

      
    },

    updated() {
      this.dialog === false ? this.dialog = true : this.dialog = true; 
    },
}
</script>


<style lang="scss" scoped>
    
</style>