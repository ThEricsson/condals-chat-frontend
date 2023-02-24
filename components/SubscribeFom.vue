<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <div class="form-group text-left">
        <label for="topic">Topic:</label>
        <input
          class="form-control"
          v-model="form.topic"
          type="text"
          name="topic"
          placeholder="Topic"
          required
        />
      </div>
      <button type="submit" class="btn btn-primary">Subscribe -></button>
    </form>
    <div class="mt-3 border rounded bg-dark" v-if="message">
      <div class="p-3 text-success text-left fw-bold">
        <span
          >condals-chat:~$ mosquitto_sub -h {{ host }} -t {{ form.topic }}</span
        >
        <p>> {{ message }}</p>
      </div>
    </div>
  </div>
</template>

<script lang="js">
import axios from "axios"
import qs from "querystring"

export default {
    name: "SubscribeForm",
    data(){
        return {
            form: {
                topic: ""
            },
            message: "",
            host: process.env.NODE_BACKEND_URL.split(":")[1].substring(2)
        }
    },
    methods: {
        handleSubmit: async function(){
            const formData = {}

            formData.topic = this.form.topic

            await axios
                .get(`${process.env.NODE_BACKEND_URL}/subscribe?` + qs.stringify(formData))
                .then(({data}) => {
                  this.message = data.message
                })
                .catch((error) => {
                  console.log(error)
                })

        }
    }

}
</script>
