<template>
  <div class="registration">
    <div class="container-fluid">
      <div class="row align-items-center">
        <div class="col-xs-12 col-lg-6 registration__inner">
          <h2 class="registration__caption">Contact Us</h2>
          <form @submit.prevent="postUser" class="registration__form" novalidate>
            <input @keypress="typeName($event)" v-model="fields.name" class="registration__field" placeholder="Name" type="text" name="name">
            <input v-model="fields.phone" class="registration__field" placeholder="Phone" type="tel" name="tel">
            <input v-model="fields.email" class="registration__field registration__field--last" placeholder="E-mail" type="email" name="email">
            <label class="registration__label">
              <input class="registration__checkbox" v-model="fields.checked" type="checkbox">
              I agree the processing of personal data
            </label>
            <button :class="[disabled === true ? 'disabled-btn' : '']" :disabled="disabled" class="registration__btn">Get in touch</button>
            <p class="registration__error" v-if="error">All field are required</p>
          </form>
        </div>
        <div class="col-xs-12 col-lg-6">
          <p class="registration__text">Please tell us more about your request and give us info about your company and country</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const patternTel = /^\+?3?8?(093\d{7})$/;

const patternEmail = /\S+@\S+\.\S+/;

export default {
  name: 'registration',
  data() {
    return {
      error: false,
      disabled: false,
      fields: {
        name: '',
        phone: '',
        email: '',
        checked: false
      }
    }
  },
  methods: {
    postUser() {
      const formData = new FormData();
      formData.append('name',this.fields.name);
      formData.append('phone',this.fields.phone);
      formData.append('email',this.fields.email);
      const fields = [...document.querySelectorAll('.registration__field')];
      const label = document.querySelector('.registration__label');
      if ( this.fields.name !== '' && this.fields.name.length <= 29 && this.fields.checked === true && patternTel.test(this.fields.phone) && patternEmail.test(this.fields.email) ) {
        this.error = false;
        this.disabled = true;
        label.classList.remove('error-label');
        fields.forEach(field => {
          field.classList.remove('error')
        });
        fetch('http://httpbin.org/post', {
          method: 'post',
          body: formData
        })
          .then(response => response.json())
            .then(data => {
              console.log(data)
            })
      } else {
        this.error = true;
        label.classList.add('error-label');
        fields.forEach(field => {
          field.classList.add('error')
        })
      }
    },
    typeName(evt) {
      if ((evt.keyCode >= 48 && evt.keyCode <= 57) || evt.keyCode === 47 || evt.keyCode === 45 || evt.keyCode === 61) {
        evt.preventDefault()
      }
    }
  }
}
</script>


<style lang="scss" scoped>

.registration {
  padding: 98px 60px;
  background: url('../assets/img/pattern.png') no-repeat center center;
  background-size: cover;
  &__caption {
    font-weight: 300;
    font-size: 34px;
    line-height: 48px;
    color: #ffffff;
    margin-bottom: 48px;
  }
  &__text {
    font-weight: 300;
    font-size: 18px;
    line-height: 34px;
    color: #000000;
  }
  &__label {
    font-weight: 300;
    font-size: 18px;
    line-height: 34px;
    color: #ffffff;
    margin-bottom: 42px;
  }
  &__form {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }
  &__btn {
    font-weight: 300;
    color: #ffffff;
    background: #262626;
    border: none;
    padding: 37px 111px;
    cursor: pointer;
    text-transform: uppercase;
  }
  &__field {
    width: 100%;
    border-width: 0px 0px 2px;
    border-color: #040707;
    border-style: solid;
    background: transparent;
    outline: none;
    line-height: 60px;
    color: #ffffff;
    transition: all .3s;
    font-weight: 300;
    font-size: 18px;
    &--last {
      margin-bottom: 21px;
    }
    &::placeholder {
      font-weight: 300;
      color: #262626;
      font-size: 18px;
    }
    &:focus {
      border-color: #ffffff;
      &::placeholder {
        transition: all .3s;
        color: #ffffff;
      }
    }
  }
  &__error {
    color: #f44336;
    font-weight: 300;
    font-size: 18px;
    line-height: 34px;
  }
}

.error {
  border-color: #f44336;
}

.error-label {
  color: #f44336
}

.disabled-btn {
  background: #BDBDBD;
  cursor: auto;
}

@media screen and(max-width: 768px) {
  .registration {
    &__inner {
      margin-bottom: 30px;
    }
  }
}

@media screen and(max-width: 576px) {
  .registration {
    padding: 38px 0;
    &__caption {
      margin-bottom: 18px;
    }
    &__btn {
      padding: 30px 51px;
    }
  }
}

</style>