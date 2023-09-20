<template>

    <div>
    <b-form @submit="onSubmit" @reset="onReset">
      <b-form-group
        id="input-group-1"
        label="Email cím:"
        label-for="input-1"
      >
        <b-form-input
          id="input-1"
          v-model="email"
          type="email"
          placeholder="Email"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Név:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="name"
          placeholder="Név"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Üzenet:" label-for="input-3">
        <b-form-textarea
          id="input=3"
          v-model="message"
          placeholder="Üzenet"
          required
        ></b-form-textarea>
      </b-form-group>

      <b-button type="submit" variant="success">Küldés</b-button>
      <b-button type="reset" variant="danger">Törlés</b-button>
    </b-form>

  </div>
  </template>

  <script>
    const WEB3FORMS_ACCESS_KEY = process.env.VUE_APP_EMAIL_SERVICE;


  export default {
    data() {
      return {
        name: "",
        email: "",
        message: "",
      };
    },
    methods: {
      async onSubmit() {
        console.log('Message:', this.message);
        const response = await fetch("https://api.web3forms.com/submit", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Accept: "application/json",
          },
          body: JSON.stringify({
            access_key: WEB3FORMS_ACCESS_KEY,
            name: this.name,
            email: this.email,
            message: this.message,
          }),
        });
        const result = await response.json();
        if (result.success) {
          console.log(result);
        }
      },
      onReset(event) {
        event.preventDefault()
        this.email = ''
        this.name = ''
        this.message = ''
    },
  },
};
  </script>