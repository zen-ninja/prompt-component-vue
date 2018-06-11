<template>
  <div id="app">
    <img src="./assets/logo.png">
    <prompt v-for="_prompt in prompt" v-bind:showPrompt="showPrompt" v-bind:key="_prompt.id" v-bind:icon="_prompt.icon" v-bind:color="_prompt.color" v-bind:msg="_prompt.title" v-bind:info="_prompt.info" v-bind:btn="_prompt.simpleContent"></prompt>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: function() {
    var showPrompt = false
    return {
      prompt: [
        {id: 1, simpleContent: false, icon: 'img/graphic-future-targets.svg', title: 'Target updated!'},
        {id: 2, simpleContent: false, icon: 'img/graphic-stream-editor.svg', title: 'Task updated!'},
        {id: 3, simpleContent: false, icon: 'img/icon-cross-circle.svg', color: '#93CC32', title: 'Changes saved.'},
        {id: 4, simpleContent: true, icon: 'img/icon-exclamation-circle.svg', color: '#ED4444', title: 'Please note', info: 'The values you have entered as future targets will be deleted if you change the frequency of this promise.'},
        {id: 5, simpleContent: true, icon: 'img/icon-line-circle.svg', title: 'Future Targets', info: "Values must be numeric, no more than 13 characters and cannot go beyond the target’s end date."},
        {id: 6, simpleContent: true, icon: 'img/icon-tick-circle.svg', color: '#13AFD7', title: 'Stream Editors', info: 'Editors can add and remove goals and members, and can change the title and report frequency.'}
      ],
      showPrompt
    }
  },
  mounted(){
    this.cyclePrompts()
  },
  methods: {
    togglePrompt: function() {
      this.showPrompt = true;
    },
    cyclePrompts: function() {
      for (var el=0;el<=6;el++) {
        setTimeout(function(){
          this.togglePrompt
        }, 3000);
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.u-flex-1 {
  flex: 1;
}

.u-flex-v {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.u-flex-h {
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn {
  padding: 1em 0;
  width: 100%;
}

.bg-blue {
  background-color: #13AFD7;
}

.u-text-uppercase {
  text-transform: uppercase;
}

.u-text-white {
  color: white;
}

.is-hidden, .u-hidden {
  display: none !important;
}

.svg {
  width: 5em;
  height: 5em;
  background-repeat: no-repeat;
  background-size: 100%;
}

.svg.color-red {
  fill: red;
}

html, body {
  margin: 0;
  padding: 0;
}

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

.item {
  cursor: pointer;
  text-decoration: underline;
}

.item:hover {
  filter: brightness(110%);
  text-decoration: none;
}

header {
  display: flex;
  align-content: center;
  justify-content: space-between;
  width: 100%;
  height: 5vh;
  background-color: #484848;
  color: white;
}

.icon {
  width: 2em;
  height: 2em;
  background-color: red;
}

nav {
  display: flex;
  justify-content: center;
}

section {
  padding: 1em;
}
</style>
