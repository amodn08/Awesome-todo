<template>
  <form @submit.prevent="submitForm">
    <div class="row q-mb-md">
      <q-banner class="bg-grey-3 col">
        <template v-slot:avatar>
          <q-icon name="account_circle" color="primary" />
        </template>
        {{ tab | titleCase }} to access your Todos anywhere!
      </q-banner>
    </div>

    <div class="row q-mb-md">
      <q-input
        v-model="formData.email"
        :rules="[
          (val) =>
            isValidEmailAddress(val) || 'Please enter valid E-mail Address',
        ]"
        ref="email"
        lazy-rules
        outlined
        class="col"
        label="Email"
        stack-label
      />
    </div>
    <div class="row q-mb-md">
      <q-input
        v-model="formData.password"
        :rules="[(val) => val.length >= 6 || 'Please use minimum 6 characters']"
        ref="password"
        lazy-rules
        type="password"
        outlined
        class="col"
        label="Password"
        stack-label
      />
    </div>
    <div class="row">
      <q-space />
      <q-btn color="primary" :label="tab" type="submit" />
    </div>
  </form>
</template>

<script>
export default {
  props: ["tab"],
  data() {
    return {
      formData: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    isValidEmailAddress(email) {
      var re =
        /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(String(email).toLowerCase());
    },
    submitForm() {
      this.$refs.email.validate();
      this.$refs.password.validate();
      if (!this.$refs.email.hasError && !this.$refs.password.hasError) {
        if (this.tab == "login") {
          console.log("login the user");
        } else {
          console.log("register the user");
        }
      }
    },
  },
  filters:{
    titleCase(value){
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
};
</script>

<style>
</style>