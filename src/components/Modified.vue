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
        return this.$store.state.code;
      },
      set(code) {
        this.$store.commit("updateCode", code);
        // this.$store.dispatch("changeCode");
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
</style>