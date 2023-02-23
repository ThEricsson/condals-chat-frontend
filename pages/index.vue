<template>
  <div>
    <h1>Condals Chat</h1>
    <div class="m-2">
      <span>
        Benvingut a Condals Chat, publica missatges amb el servei publish o
        incorporat en els topics de difusió per adonar-te de les últimes
        notícies!
      </span>
      <div class="row">
        <div class="p-1 col-md-6">
          <button class="btn btn-primary">
            <nuxt-link class="text-white" to="/publish">Publish</nuxt-link>
          </button>
        </div>
        <div class="p-1 col-md-6">
          <button class="btn btn-primary">
            <nuxt-link class="text-white" to="/subscribe">Subscribe</nuxt-link>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
};
</script>
