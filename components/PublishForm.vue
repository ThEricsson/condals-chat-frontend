<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <input />
    </form>
  </div>
</template>

<script lang="js">
import axios from "axios"

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
        handleSubmit: async function(){
            const formData = new FormData();
        }
    }
}
</script>
