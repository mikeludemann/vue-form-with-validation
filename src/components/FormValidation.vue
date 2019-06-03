<template lang="html">

  <section class="form-validation">

    <form id="validForm" @submit="validationForm" action="#" method="post" novalidate="true">
      <div v-if="errors.length" class="error">
        <div>Correct the following error(s):</div>
        <div>
          <ul>
            <li v-for="error in errors">{{ error }}</li>
          </ul>
        </div>
      </div>
      <div>
        <div>
          <label for="firstname">First Name:</label>
        </div>
        <div>
          <input id="firstname" v-model="firstname" type="text" name="firstname">
        </div>
      </div>
      <div>
        <div>
          <label for="lastname">Last Name:</label>
        </div>
        <div>
          <input id="lastname" v-model="lastname" type="text" name="lastname">
        </div>
      </div>
      <div>
        <div>
          <label for="email">E-Mail</label>
        </div>
        <div>
          <input id="email" v-model="email" type="email" name="email">
        </div>
      </div>
      <div>
        <div>
          <label for="eat">Eat</label>
        </div>
        <div>
          <select id="eat" v-model="eat" name="eat">
            <option value="ice">Ice</option>
            <option value="pizza">Pizza</option>
            <option value="salad">Salad</option>
          </select>
        </div>
      </div>
      <div>
        <input class="button--style" type="submit" value="Submit">
      </div>
    </form>

  </section>

</template>

<script lang="js">
  export default  {
    name: 'FormValidation',
    props: [],
    mounted() {

    },
    data() {
      return {
        errors: [],
        firstname: null,
        lastname: null,
        email: null,
        eat: null
      }
    },
    methods: {
      validationForm: function (e) {

        this.errors = [];

        if (!this.firstname) {

          this.errors.push("First Name is required.");

        }

        if (!this.lastname) {

          this.errors.push("Last Name is required.");
          
        }

        if (!this.email) {

          this.errors.push('E-Mail required.');

        } else if (!this.validationEmail(this.email)) {

          this.errors.push('Your E-Mail is not valid.');

        }

        if (!this.errors.length) {

          return true;

        }

        e.preventDefault();

      },
      validationEmail: function (email) {

        var regexp = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
        
        return regexp.test(email);

      }
    },
    computed: {

    }
}
</script>

<style scoped lang="scss">
  .form-validation {
    width: 300px;
    margin: auto;
    transition: all 1s ease-in-out;
  }

  ul {
    padding-left: 20px !important;
    text-align: left;
  }

  #validForm {
    text-align: left;
  }

  input,
  label,
  select {
    width: 100%;
    margin: 10px 0px;
  }

  input[type=submit] {
    -webkit-appearance: none;
    -moz-appearance: none;
    -ms-appearance: none;
    -o-appearance: none;
    appearance: none;
  }

  .button--style {
    color: #fff;
    background-color: #0d0;
    padding: 10px;
    border: 0.5px solid #ccc;
  }

  .error {
    color: #f00;
    transition: all 1s ease-in-out;
  }
</style>
