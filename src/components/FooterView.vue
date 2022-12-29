<template>
  <v-footer>
      <v-card
        elevation="0"
        rounded="0"
        width="100%"
        class="bg-grey text-center"
      >
        <v-card-text>
          <v-btn
            class="mx-4"
            icon="fab fa-linkedin-in"
            variant="plain"
            color="white"
            href="https://www.linkedin.com/in/xinyu-chen-8123b218a/"
          ></v-btn>
          <v-btn
            class="mx-4"
            icon="fab fa-github"
            variant="plain"
            color="white"
            href="https://github.com/acrophobeee"
          ></v-btn>
        </v-card-text>

        <v-card-text class="text-white">
          @ {{ new Date().getFullYear() }} — Xinyu Chen
          <strong></strong>
        </v-card-text>
      </v-card>
    </v-footer>
</template>

<script>
export default {
}
</script>

<style>
.v-footer {
  padding: 8px 0 !important;
}
</style>