<template>
  <div class="formElements">
    <h2>Registration Form</h2>
    <div class="container"> 
       <div class="form-input">
        <!-- <p v-if="hasError" class="error">{{ error }}</p> -->
        <form>
          <p v-if="hasError" class="error">{{ error }}</p>
          <input type="text" placeholder="First Name ..." required v-model="firstName">
          <input type="text" placeholder="Last Name ..." required v-model="lastName">
          <input type="email" placeholder="Enter your Email here..." required v-model="mail">
          <input type="number"  placeholder="Phone Number" required v-model="phoneNumber">
          <input type="password" placeholder="Enter password here" v-model="pword">
          <button type="submit" class="submit" @click.prevent="handleSubmission">Submit</button>
       </form> 
       </div>
       <div class="form-output" v-if="isValid">
          <p>First Name:{{ firstName }}</p>
          <p>Last Name:{{ lastName }}</p>
          <p>Full Name:{{ firstName }}  {{ lastName }}</p>
          <p>Email: {{ mail }}</p>
          <p>Number: {{ phoneNumber }}</p>
          <p>Password: {{ pword }}</p>
         <button @click="handleClose">Ok</button>
       </div>
      </div>
  </div>
</template>

<script>
import { isValid } from 'ipaddr.js'

export default {
  name: 'formElements',
  data(){
    return{
      firstName:'',
      lastName:'',
      mail:'',
      phoneNumber:'',
      pword:'',
      error:'',
      hasError:false,
      isValid:true
    }
  },
  methods:{
    handleSubmission(){
      if(!this.firstName || !this.lastName ){
        this.hasError = true
        this.error = "Pls fill the form"
      }
      else if(this.firstName.length<3 || this.firstName.length<3){
        this.hasError=true
        this.error="Name has to be more than 3 characters"
      }
      else if(this.phoneNumber.length>11){
        this.hasError=true
        this.error="Invalid phone number"
      }
      else if(this.pword.length<7){
        this.hasError=true
        this.error="Password must be more than 6 characters"
      }
      else{
        this.isValid =true
        this.hasError=false
      }
    },
    handleClose(){
      this.isValid=false
    }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  *{
    padding:0;
    margin: 0;
  }
  body{
    background: rgb(73, 72, 72);
  }
  h2{
    text-align: center;
    padding:20px;
    font-size:2em;
    font-weight: lighter;
    background: rgb(230, 230, 230);
  }
.container{
  width:100%;
  height:90vh;
  display:flex;
  justify-content: center;
  background: rgb(230, 230, 230);
  
}
.form-input, .form-output{
  width:40%;
}
.error{
  background: #fff;
  padding:10px;
  color:red;
  width:50%;
  border-radius: 5px;
  margin-left:20px;
  margin-top:60px;
}
form, .form-output{
    display:flex;
    flex-direction: column;
    justify-content: center;
    height: 80vh;
}
input[type="text"], input[type="email"] ,input[type="password"],input[type="number"]{
    margin:15px 20px;
    width:50%;
    border:none;
    border-radius: 7px;
    padding:13px ;

  }
.form-output >p{
  background: #fff;
  padding:10px;
  margin: 10px;
  width:60%;
  border-radius:7px;
}
.form-output > button{
  border:none;
    padding :10px;
    width:30%;
    margin:10px 10px;
    border-radius:5px;
    cursor:pointer;
    color:#fff;
    background: rgb(235, 32, 32);
}
 .submit{
    border:none;
    padding :10px;
    width:30%;
    margin:10px 20px;
    border-radius:5px;
    cursor:pointer;
    color:#fff;
    background: rgb(32, 32, 235);
  }
</style>
