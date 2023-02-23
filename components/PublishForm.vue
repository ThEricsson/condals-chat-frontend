<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <div class="form-group text-left">
        <label for="topic">Topic</label>
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
        <label for="message">Missatge</label>
        <input
          class="form-control"
          v-model="form.message"
          type="text"
          name="message"
          placeholder="Missatge"
          required
        />
      </div>
      <button type="submit" class="btn btn-primary">Publicar</button>
    </form>
  </div>
</template>

<script lang="js">
import axios from "axios"

console.log(`Node URL: ${process.env.NODE_BACKEND_URL}`)

export default {
    name: "PublishForm",
    data() {
        return {
            form: {
               topic: "",
               message: "",
            },
        };
    },
    methods: {
        //Al hacer clic en submit, la información se guarda en un objeto con las claves del formulario para despues enviarlo por axios.
        handleSubmit: async function(){
            const formData = new FormData();

            for (let [key, value] of Object.entries(this.form)){
                formData.append(key, value)

            }

            await axios
                .get(`http://localhost:3700/publish`, formData)
                .then(({data}) => {
                    console.log(data)
                })
                .catch((error) => {
                    console.log(error)
                })
        }
    }
}
</script>
