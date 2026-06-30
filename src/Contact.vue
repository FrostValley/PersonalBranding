<template>
<div class="contact-wrapper">
  <div class="contact-content">
    <div style="text-align:left">
      <h1>Contact me</h1>
    </div>
    <div class="section-divider"></div>
    <div class="row">
      <div class="column-right">
        <fieldset>
          <form @submit.prevent="sendEmail">
            <p>Hier kunt u contact met mij opnemen. Ik zal zo snel mogelijk antwoord geven.</p>

            <label for="fname">Name</label>
            <input
              type="text"
              id="fname"
              v-model="form.name"
              placeholder="Your name..."
              required
            >

            <label for="email">Email</label>
            <input
              type="email"
              id="email"
              v-model="form.email"
              placeholder="Your email..."
              required
            >

            <label for="subject">Message</label>
            <textarea
              id="subject"
              v-model="form.message"
              placeholder="Write something..."
              style="height:170px"
              required
            ></textarea>

            <input type="submit" value="Submit">
          </form>
        </fieldset>
      </div>
    </div>
  </div>
</div>

</template>

<script>
import emailjs from "@emailjs/browser";

export default {
  data() {
    return {
      form: {
        name: "",
        email: "",
        message: "",
      },
    };
  },

  methods: {
    sendEmail() {
      const templateParams = {
        from_name: this.form.name,
        from_email: this.form.email,
        message: this.form.message,
      };

      emailjs
        .send(
          "service_9mgetup",
          "template_mxbt08k",
          templateParams,
          "stqbzYdK4nnabEgqx"
        )
        .then(() => {
          alert("Message sent successfully!");

          this.form.name = "";
          this.form.email = "";
          this.form.message = "";
        })
        .catch((error) => {
          console.error(error);
          alert("Failed to send message.");
        });
    },
  },
};
</script>