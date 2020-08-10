<template>
  <div ref="app">
    <!-- Navigation Bar -->
    <nav
      class="navbar is-info add-space has-shadow"
      role="navigation"
      aria-label="main navigation"
    >
      <!-- CyberAtlas Logo -->
      <div class="navbar-brand">
        <figure class="image is-64x64">
          <img src="./assets/cyberatlas.png" />
        </figure>
        <a class="navbar-item">
          <h1 class="title" style="color:#fff;">
            CyberAtlas
          </h1>
        </a>
        <a
          role="button"
          class="navbar-burger burger"
          aria-label="menu"
          aria-expanded="false"
          data-target="navbarBasicExample"
          @click="burgerToggle = !burgerToggle"
        >
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>
      <div class="navbar-menu" v-bind:class="{ 'is-active': burgerToggle }">
        <div class="navbar-start">
          <div class="navbar-item">
            Hello
          </div>
        </div>
        <div class="navbar-end">
          <!-- Performance Modal Button -->
          <div class="navbar-item">
            <button
              class="button is-info is-medium"
              @click="darkMode = !darkMode"
            >
              <strong>
                {{ darkMode ? "Dark" : "Light" }}
              </strong>
            </button>
          </div>
          <!-- Performance Modal Button -->
          <div class="navbar-item">
            <button class="button is-info is-medium">
              <strong>
                Performance
              </strong>
            </button>
          </div>
          <!-- Performance Modal -->
          <!-- Documentation Link Button -->
          <div class="navbar-item">
            <button class="button is-info is-medium" @click="openDocs">
              <strong>
                Documentation
              </strong>
            </button>
          </div>
        </div>
      </div>
    </nav>
    <router-view />
    <!-- Footer -->
    <footer class="footer">
      <div class="content has-text-centered">
        <p>
          <strong>CyberAtlas</strong> by
          <!-- Personal Email Link -->
          <a href="mailto:brownfield.david@mail.mil">David Brownfield </a>
          . The source code is licensed
          <!-- Source Code License -->
          <a href="https://choosealicense.com/licenses/gpl-3.0/">GNU GPLv3</a>.
          The website content is licensed
          <!-- Website License -->
          <a href="http://creativecommons.org/licenses/by-nc-sa/4.0/"
            >CC BY NC SA 4.0</a
          >.
        </p>
      </div>
    </footer>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  data: () => ({
    burgerToggle: false,
    darkMode: false
  }),
  watch: {
    darkMode() {
      this.$refs.app.dataset.theme = this.darkMode ? "dark" : "light";
    }
  }
});
</script>
<style lang="scss">
@import "~bulma/sass/utilities/_all";

// Set your colors
$info: #167df0;
$primary-invert: findColorInvert($info);

// Setup $colors to use as bulma classes (e.g. 'is-twitter')
$colors: (
  "white": (
    $white,
    $black
  ),
  "black": (
    $black,
    $white
  ),
  "light": (
    $light,
    $light-invert
  ),
  "dark": (
    $dark,
    $dark-invert
  ),
  "primary": (
    $primary,
    $primary-invert
  ),
  "info": (
    $info,
    $info-invert
  ),
  "success": (
    $success,
    $success-invert
  ),
  "warning": (
    $warning,
    $warning-invert
  ),
  "danger": (
    $danger,
    $danger-invert
  )
);

@import "~bulma";
[data-theme="dark"] {
  @import "~bulma-prefers-dark/sass/utilities/_all";
  @import "~bulma-prefers-dark/sass/base/_all";
  @import "~bulma-prefers-dark/sass/elements/_all";
  @import "~bulma-prefers-dark/sass/components/_all";
  @import "~bulma-prefers-dark/sass/layout/_all";
  background-color: #0a0a0a;
}
.add-space {
  padding: 0.25em 0.5em 0em 0.5em;
}
.title {
  margin-top: -0.25em;
}
</style>
