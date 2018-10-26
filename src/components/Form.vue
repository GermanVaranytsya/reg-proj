<template>
  <div class="uk-background-default uk-padding ">
    <form id="app"
          @submit="checkForm"
          action="https://vuejs.org/"
          method="post" class="uk-padding-large">
      <fieldset class="uk-fieldset">

        <legend class="uk-legend uk-text-primary uk-text-bold">REGISTRATION</legend>

        <div class="uk-margin">
          <h6>Fill all the fields below.</h6>
        </div>

        <div class="uk-margin">
          <input class="uk-input"
                 id="email"
                 v-model="email"
                 type="email"
                 name="email"
                 placeholder="Enter your email"
                 autocomplete="new-email">
        </div>

        <div class="uk-margin">
          <input class="uk-input"
                 id="password"
                 v-model="password"
                 type="password"
                 name="password"
                 placeholder="Enter your password"
                 autocomplete="new-password">
        </div>

        <div class="uk-margin">
          <button class="uk-input uk-button uk-button-primary" type="submit" value="CREATE ACCOUNT">
            <span class="uk-margin-small-right" uk-icon="lock"></span>CREATE ACCOUNT
          </button>
        </div>

        <div class="uk-margin uk-text-center">
          <p style="font-size: 13px">By signing i accept with <a href="#"> Terms and Conditions </a>
          </p>
        </div>
        <div v-if="errors.length" class="uk-margin-auto">
          <hr>
          <ul>
            <li class="uk-text-danger uk-h4" v-for="error in errors">{{ error }}</li>
          </ul>
        </div>

      </fieldset>
    </form>
  </div>
</template>

<script>

  export default {
    data: function () {
      return {
        errors: [],
        email: null,
        password: null
      }
    },
    methods: {
      checkForm: function (e) {
        this.errors = [];
        if (!this.email) {
          this.errors.push("Email required.");
        } else if (!this.validEmail(this.email)) {
          this.errors.push("Valid email required.");
        } else if (!this.password) {
          this.errors.push("Password required");
        } else if (!this.validPassword(this.password)) {
          this.errors.push("Password requirements: minimum 8 characters, 1 letter, 1 number, 1 special symbol ");
        }
        if (!this.errors.length) return true;
        e.preventDefault();
      },
      validEmail(email) {
        var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
        return re.test(email);
      },
      validPassword(s) {
        if (!s || s.length < 8) {
          return false;
        }
        if (!/[0-9]/.test(s)) {
          return false;
        }
        if (!/[a-z]/.test(s)) {
          return false;
        }
        if (!/[@#$&*^%!+=\/\\[\]|?.,<>)(;:'"~`]/.test(s)) {
          return false;
        }
        return true;
      }
    }
  }

</script>

<style>
  .uk-text-primary {
    color: #70b6e2 !important;
  }

  .uk-link:hover, a:hover {
    color: #5b93b7;
    text-decoration: underline;
  }

  .uk-link, a {
    color: #70b6e2;
    text-decoration: none;
    cursor: pointer;
  }

  .uk-button-primary {
    background-color: #70b6e2;
  }

  .uk-button-primary:focus, .uk-button-primary:hover {
    background-color: #5b93b7;
  }
</style>
