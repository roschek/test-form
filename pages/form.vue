<template>
  <div class="container">
 <h1 class="form__title">Заполните форму чтобы вернуться обратно</h1>
    <form @submit.prevent="onSubmit">
      <div class="form-item" :class="{ errorInput: $v.email.$error }">
        <input  class="form-input" type="text" placeholder="введите имя" v-model="name" :class="{error:$v.name.$error }" @change="$v.name.$touch()">
<!--        <span class="error" v-if="!$v.name.required">Это обязательное поле</span>-->
        <span class="error" v-if="!$v.name.minLength">маловато букв</span>
        <span class="error" v-if="!$v.name.maxLength">перебор с буквами</span>
      </div>

      <div class="form-item" :class="{ errorInput: $v.email.$error }">
        <input  class="form-input" type="email" placeholder="введите E-mail" v-model="email" :class="{error:$v.email.$error }" @change="$v.email.$touch()">
<!--        <span class="error" v-if="!$v.email.required">Это обязательное поле</span>-->
        <span class="error" v-if="!$v.email.email">Введите корректный е-майл</span>
      </div>
      <textarea class="form-input form-input-textarea" name="textarea" id="" cols="30" rows="5"></textarea>
      <div class="form-item" :class="{ errorInput: $v.email.$error }">
        <input v-phone class="form-input" type="tel" placeholder="+7(___)___-__-__"  autocomplete="tel" v-model="phone" :class="{error:$v.phone.$error }" @change="$v.phone.$touch()">

      </div>

      <button type="submit"  class="form__submit" :disabled="$v.$invalid">Вернуться на главную</button>

    </form>

  </div>
</template>

<script>
import { required, email,minLength, maxLength,numeric} from 'vuelidate/lib/validators'

export default {
  data(){
    return{
      email: '',
      name:'',
      phone:'',
      submitStatus: null
    }
  },
  validations: {
    email:{
      required,
      email
    },
    name:{
      required,
      minLength: minLength(6),
      maxLength: maxLength(40)
    },
     phone:{
      required

    }

  },
  methods:{
    onSubmit(){
this.$router.push('/')
      }
  }
}
</script>

<style scoped>
.container{
  max-width: 800px;
  border:1px solid lavender;
  margin:200px auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
}
.form__title{
  margin-top: 30px;
  margin-bottom: 40px;
}
.form-item{
  display: flex;
  flex-direction: column;
}
.form-input{
  padding:10px 20px;
  border:1px solid lavender;
  margin-top: 30px;
}
.form-item {
  color: black;
}
.error{
  color: red;
  font-size: 14px;
}
.form__submit{
  margin-top: 30px;
  padding:10px 20px;
  background-color: #1DE9B6;
  cursor: pointer;
  border: none;
  border-radius: 5px;
  margin-bottom: 30px;
}
.form-input-textarea{
  max-width: 400px;
  margin-bottom: 20px;
}
</style>
