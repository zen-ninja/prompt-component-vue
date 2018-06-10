<template>
  <div class="prompt-wrapper u-flex-h" v-bind:class="{ activatePrompt: 'is-hidden' }">
    <div class="prompt_content u-flex-v">
      <div class="u-flex-v u-flex-1">
        <div class="svg">{{ icon }}</div>
        <div class="msg"><h2>{{ msg }}</h2></div>
        <div class="info"><p>{{ info }}</p></div>
      </div>
      <div v-on:click="closePrompt()" class="btn bg-blue u-flex-h u-text-uppercase u-text-white" v-bind:class="{ simpleContent: 'is-hidden' }">Got it</div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Prompt",
  // data() {
  //   var icon,
  //     msg,
  //     info,
  //     color = "#000",
  //     activePrompt = false;
  // },
  props: ['icon', 'msg', 'info', 'color', 'activePrompt' ],
  methods: {
    promptUser: function(msg) {
      activatePrompt();
      if (
        msg === "Target updated!" ||
        msg === "Task updated!" ||
        msg === "Changes saved."
      ) {
        simpleContent();
      }

      if (msg === "Target updated!" || msg === "Task updated!") {
        stuffUpdated();
      }

      if (msg === "Changes saved.") {
        changesSaved();
      }

      if (msg === "Please note") {
        note();
      }

      if (msg === "Future Targets") {
        targets();
      }

      if (msg === "Stream Editors") {
        editors();
      }
    },
    activatePrompt: function() {
      if (PROMPT_EL.classList.contains("is-hidden")) {
        PROMPT_EL.classList.remove("is-hidden");
        activePrompt = true;
      } else {
        activePrompt = false;
      }
    },
    simpleContent: function() {
      if (
        !BUTTON_EL.classList.contains("is-hidden") &&
        MESSAGE_EL.classList.contains("is-hidden")
      ) {
        BUTTON_EL.classList.add("is-hidden");
        MESSAGE_EL.classList.add("is-hidden");
      }
    },
    stuffUpdated: function() {
      icon = "icon-tick-circle";
      color = "#93CC32";
      insertContent(icon, msg, color, info);
    },
    editors: function() {
      icon = "graphic-stream-editor";
      msg =
        "Editors can add and remove goals and members, and can change the title and report frequency.";
      insertContent(icon, msg, color, info);
    },
    targets: function() {
      icon = "graphic-future-targets";
      msg =
        "Values must be numeric, no more than 13 characters and cannot go beyond the target’s end date.";
      insertContent(icon, msg, color, info);
    },
    note: function() {
      icon = "icon-exclamation-circle";
      msg =
        "The values you have entered as future targets will be deleted if you change the frequency of this promise.";
      color = "#ED4444";
      insertContent(icon, msg, color, info);
    },
    changesSaved: function() {
      icon = "icon-tick-circle";
      color = "#13AFD7";
      insertContent(icon, msg, color, info);
    },
    closePrompt: function() {
      if (!PROMPT_EL.classList.contains("is-hidden")) {
        PROMPT_EL.classList.add("is-hidden");
      }
    },
    insertContent: function(icon, msg, color, info) {
      ICON_EL.classList.add(icon);
      ICON_EL.classList.add("color-red");
      MESSAGE_TITLE.innerHTML = msg;
      INFO_PARAGRAPH.innerHTML = info;
    }
  }
};
</script>
<style scoped>
.prompt-wrapper {
  width: 100%;
  height: 100vh;
  background: rgba(0, 0, 0, 0.8);
  position: absolute;
  z-index: 999;
  top: 0;
  left: 0;
}

.prompt-wrapper .prompt_content {
  background-color: #fff;
  border-radius: 5px;
  width: 95%;
  height: 95%;
}

@media screen and (min-width: 1024px) {
  .prompt-wrapper .prompt_content {
    width: 95%;
    height: 90%;
  }
}
</style>
