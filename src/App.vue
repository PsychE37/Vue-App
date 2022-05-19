<template>
  <v-app>
    <v-app-bar app color="white" dark>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          contain
          src="https://codedrills.io/meta_banner.png"
          transition="scale-transition"
          max-width="2.4%"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <component :is="currentView" />
    </v-main>
  </v-app>
</template>

<script>
import Scoreboard from "./components/ScoreBoard";
import Submission from "./components/SubmissionPage";

const routes = {
  "/scoreboard": Scoreboard,
  "/submissions/": Submission,
  "/submissions": Submission,
};

export default {
  data() {
    return {
      currentPath: window.location.href.replace("http://localhost:8080/", "/"),
    };
  },
  computed: {
    currentView() {
      return routes[this.currentPath || "/"];
    },
  },
  mounted() {
    window.addEventListener("hashchange", () => {
      this.currentPath = window.location.href.replace(
        "http://localhost:8080/",
        "/"
      );
    });
  },
};
</script>

<style>
tbody tr:nth-of-type(even) {
  background-color: rgba(236, 237, 237);
}

tbody tr:nth-of-type(odd) {
  background-color: rgb(250, 250, 250);
}

.v-data-table-header {
  background-color: rgba(182, 183, 187);
}

.v-data-footer {
  background-color: rgb(250, 250, 250);
}

.theme--light.v-data-table thead tr th {
  color: white;
}
</style>
