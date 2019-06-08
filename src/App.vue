<template>
  <Layout :title="title">
    <Editor slot="editor"></Editor>
    <Modified slot="modified"></Modified>
    <Slider slot="slider"></Slider>
    <Controls slot="controls"></Controls>
    <Errors slot="errors"></Errors>
    <Navigation slot="navigation"></Navigation>
  </Layout>
</template>

<script>
import Layout from "./components/Layout";
import Editor from "./components/Editor";
import Modified from './components/Modified'
import Controls from "./components/Controls";
import Slider from "./components/Slider";
import Errors from "./components/Errors";
import Navigation from './components/Navigation';

export default {
  name: "app",
  props: ["title"],
  components: { Layout, Editor, Modified, Controls, Slider, Errors, Navigation }
};
</script>

<style module>
html, body {
  width: 100%;
  height: 100%;
  font-size: 14px;
  font-family: Arial, Helvetica, sans-serif;
  --gray: #bbbbbb;
}
</style>
