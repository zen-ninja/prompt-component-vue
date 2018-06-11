<template>
  <div class="prompt-wrapper u-flex-h" v-bind:class="{ 'is-ahidden': !showPrompt }">
    <div class="prompt_content u-flex-v">
      <div class="u-flex-v u-flex-1">
        <div class="svg" v-bind:style="{fill:+color+';','background-image':'url( /static/' +icon+')'}"></div>
        <div class="msg"><h2>{{ msg }}</h2></div>
        <div class="info"><p>{{ info }}</p></div>
      </div>
      <div v-on:click="closePrompt()" class="btn bg-blue u-flex-h u-text-uppercase u-text-white" v-bind:class="{ 'is-hidden': simpleContent }">Got it</div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Prompt",
  props: ['icon', 'msg', 'info', 'color'],
  data: function() {
    var showPrompt = false, simpleContent = false
    var svgStyle = {
      color: '',
      img: ''
    }
    return {
      showPrompt, simpleContent, svgStyle
    }
  },
  methods: {
    closePrompt: function() {
      this.showPrompt = false;
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
