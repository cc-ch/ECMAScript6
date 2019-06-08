<template>
  <div :class="$style.container">
    <header :class="$style.header">
      <h1 :class="$style.headerItem">{{title}}</h1>
      <div :class="$style.headerItem">
        <!-- <a href="https://github.com/boopathi/babel-time-travel" target="_blank">
          <img src="//cdnjs.cloudflare.com/ajax/libs/octicons/4.4.0/svg/mark-github.svg" width="24" height="24" />
        </a> -->
      </div>
      <div :class="$style.controls">
        <slot name="controls"></slot>
      </div>
    </header>
    <main :class="$style.main">

      <div :class="$style.navigation">
        <slot name="navigation"></slot>
      </div>

      <div :class="$style.content">
        <div :class="$style.editor">
          <slot name="modified"></slot>
        </div>
        <div :class="$style.errors">
          <slot name="errors"></slot>
        </div>
        <!-- <div :class="$style.slider">
          <slot name="slider"></slot>
        </div> -->
      </div>
      

      <div :class="$style.result">
        <div :class="$style.editor">
          <slot name="editor"></slot>
        </div>
        <!-- <div :class="$style.errors">
          <slot name="errors"></slot>
        </div> -->
        <div :class="$style.slider">
          <slot name="slider"></slot>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "app-layout",
  props: ["title"]
};
</script>

<style module>
.container {
  --width: 100%;
  --height: calc(100% - 70px);
  height: 100%;
}

.header {
  width: var(--width);
  margin: 0 auto;
  display: flex;
  flex-direction: row;
  align-items: center;
  color: black;
  border: solid 1px white;
}

.headerItem {
  padding: 0 10px;
}

.header h1 {
  font-size: 1.5em;
  font-weight: 100;
  width: 250px;
}

.main {
  width: 100%;
  box-sizing: border-box;
  /* display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center; */
  margin-bottom: 20px;
  position: relative;
  height: calc(100% - 150px);
  /* padding-left: 250px; */
}

.navigation {
  width: 240px;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
} 

.content {
  width: calc((100% - 280px)/2);
  margin-left: 250px;
  height: 100%;
  float: left;
}

.controls {
  width: 100%;
}

.slider {
  width: 100%;
  border: solid 1px var(--gray);
}

.editor {
  border: solid 1px var(--gray);
  border-bottom: 0;
  width: 100%;
  height: var(--height);
}

.editor :global(.CodeMirror) {
  width: 100%;
  height: 100%;
}
.result {
  width: calc((100% - 280px)/2);
  margin-right: 20px;
  height: 100%;
  float: right;
}
.errors {
  width: 100%;
  position: relative;
}
.content .editor {
  height: 100%;
  border: solid 1px var(--gray);
}
</style>
