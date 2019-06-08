<template>
  <codemirror v-model="code" :options="editorOptions">
  </codemirror>
</template>

<script>
import { codemirror } from "vue-codemirror-lite";
import "codemirror/mode/javascript/javascript";

export default {
  data() {
    return {
      editorOptions: {
        mode: "javascript",
        tabSize: 2,
        lineNumbers: true,
        line: true,
        foldGutter: true,
        lineWrapping: true
      }
    };
  },
  computed: {
    code: {
      get() {
        return this.$store.state.transitions[this.$store.state.current].code;
      },
      set(code) {
        this.$store.commit("updateSource", code);
      }
    }
  },
  components: {
    codemirror
  }
};
</script>

<style>
  .vue-codemirror-wrap {
    width: 100%;
    height: 100%;
  }
  .CodeMirror-scroll{
    margin-right: 0!important;
  } 
</style>