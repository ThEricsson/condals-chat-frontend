<template>
  <nav class="mb-3 navbar navbar-expand-lg navbar-dark bg-dark">
    <span class="navbar-brand">Condals Chat</span>
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active">
          <NuxtLink class="nav-link" to="/">Home</NuxtLink>
        </li>
        <li class="nav-item">
          <NuxtLink class="nav-link" to="/publish">Publish</NuxtLink>
        </li>
        <li class="nav-item">
          <NuxtLink class="nav-link" to="/subscribe">Subscribe</NuxtLink>
        </li>
      </ul>
    </div>
  </nav>
</template>
