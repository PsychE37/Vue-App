<template>
  <div class="body">
    <v-card>
      <v-card-title> Submission Details </v-card-title>
      <v-data-table
        :headers="Headers"
        :items="Details"
        hide-default-footer
      ></v-data-table>
    </v-card>
    <div class="editor">
      <v-card>
        <div class="header">
          <div class="title">
            <v-card-title> Code </v-card-title>
            <v-spacer></v-spacer>
          </div>
          <div class="options">
            <v-select
              :items="Themes"
              :menu-props="{ offsetY: true }"
              label="Editor Theme"
              @change="changeTheme"
              id="theme"
              outlined
              v-model="selected"
            ></v-select>
            <div class="button">
              <v-btn color="#ffff" elevation="0" @click="copyToClipboard">
                COPY
              </v-btn>
            </div>
          </div>
        </div>
        <div class="code">
          <textarea v-model="Content" id="editor"></textarea>
        </div>
      </v-card>
    </div>
  </div>
</template>

<script>
import * as CodeMirror from "codemirror";
import { mdiContentCopy } from "@mdi/js";
import "codemirror/addon/runmode/colorize.js";
import "codemirror/lib/codemirror.css";

import "codemirror/theme/shadowfox.css";
import "codemirror/theme/yeti.css";
import "codemirror/theme/zenburn.css";
import "codemirror/theme/midnight.css";
import "codemirror/theme/rubyblue.css";
import "codemirror/theme/eclipse.css";
import "codemirror/theme/darcula.css";
import "codemirror/theme/cobalt.css";
import "codemirror/theme/dracula.css";
import "codemirror/theme/solarized.css";
import "codemirror/theme/monokai.css";

import "codemirror/mode/clike/clike.js";
import "codemirror/mode/javascript/javascript.js";

export default {
  data() {
    return {
      Headers: [
        {
          text: "Subimission ID",
          align: "start",
          value: "id",
          sortable: false,
        },
        { text: "Submitted On", value: "time", sortable: false },
        { text: "Submitted By", value: "user", sortable: false },
        { text: "Problem", value: "problem", sortable: false },
        { text: "Language", value: "language", sortable: false },
        { text: "Status", value: "status", sortable: false },
        { text: "Score", value: "score", sortable: false },
        { text: "Time(ms)", value: "time", sortable: false },
        { text: "Memory(KiB)", value: "memory", sortable: false },
      ],
      Details: [
        {
          id: 134926,
          user: "User 1",
          problem: "Vue App",
          language: "C++",
          status: "Accepted",
          score: "100%",
          time: "2/27/2022, 5:34:42 PM",
          memory: "2493",
        },
      ],
      Content:
        '#include <iostream>\nusing namespace std;\nint main()\n{\n\tcout << "Vue App";\n\treturn 0;\n}\n',
      Themes: [
        "Cobalt",
        "Darcula",
        "Dracula",
        "Eclipse",
        "Monokai",
        "Midnight",
        "Rubyblue",
        "Solarized",
        "Shadowfox",
        "Yeti",
        "Zenburn",
      ],
      icons: { mdiContentCopy },
      selected: "Dracula",
    };
  },
  mounted() {
    this.cm = CodeMirror.fromTextArea(document.getElementById("editor"), {
      lineNumbers: true,
      theme: "dracula",
      model: "clike",
      readOnly: true,
    });
  },
  methods: {
    changeTheme(event) {
      this.cm.setOption("theme", event.toLowerCase());
    },
    copyToClipboard() {
      navigator.clipboard.writeText(this.Content);
    },
  },
};
</script>

<style scoped>
.body {
  margin: 1%;
  background-color: #ffff;
  flex-direction: row;
  justify-content: flex-end;
}
.editor {
  padding-top: 1%;
}
.header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin-bottom: -1.5%;
}
.title {
  margin-top: -1%;
}
.options {
  margin-top: 1%;
  display: flex;
}
.button {
  margin-top: 1.7%;
}
</style>
