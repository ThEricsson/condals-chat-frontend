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
      <div class="form-group text-left">
        <label for="message">Missatge:</label>
        <input
          class="form-control"
          v-model="form.message"
          type="text"
          name="message"
          placeholder="Missatge"
          required
        />
      </div>
      <button type="submit" class="btn btn-primary">Publicar -></button>
    </form>
    <div class="mt-3 border rounded bg-dark" v-if="response">
      <div class="p-3 text-success text-left fw-bold">
        <span
          >condals-chat:~$ mosquitto_pub -h {{ host }} -t {{ form.topic }} -m
          "{{ form.message }}"</span
        >
        <p>> {{ response }}</p>
      </div>
    </div>
  </div>
</template>

<script lang="js">
import axios from "axios"
import qs from 'querystring';

export default {
    name: "PublishForm",
    data() {
        return {
            form: {
               topic: "",
               message: "",
            },
            response: "",
            host: process.env.NODE_BACKEND_URL.split(":")[1].substring(2)
        };
    },
    methods: {
        //Al hacer clic en submit, la información se guarda en un objeto con las claves del formulario para despues enviarlo por axios.
        handleSubmit: async function(){
            const formData = {}

            Object.entries(this.form).forEach(([key, value]) => {
              formData[key] = value
            });

            await axios
                // .get(`${process.env.NODE_BACKEND_URL}/publish?topic=${formData.get("topic")}&message=${formData.get("message")}`)
                .get(`${process.env.NODE_BACKEND_URL}/publish?` + qs.stringify(formData))
                .then(({data}) => {
                    this.response = data.response
                })
                .catch((error) => {
                    console.log(error)
                })
        }
    }
}
</script>
