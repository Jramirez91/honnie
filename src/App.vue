<template>
  <div id="app">
    <Heart/>
    <router-view/>
  </div>
</template>

<script>
import Heart from "@/components/Heart.vue";
export default {
  components: {
    Heart
  }
};
</script>

<style lang="scss">
@import url(https://fonts.googleapis.com/css?family=Shadows+Into+Light);
#app {
  font-family: "Shadows Into Light", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: whitesmoke;
}

.tool-tip {
  border: 1px solid #ccc;
  padding: 5px 15px;
  position: relative;
  cursor: pointer;
  margin: 0 10px;
  text-transform: uppercase;
}

.tool-tip::after {
  background-color: #323a45;
  border-radius: 2px;
  color: #fff;
  content: attr(data-tooltip-title) " ";
  font-weight: normal;
  min-width: 100px;
  padding: 5px 8px;
  text-align: center;
  text-transform: none;
}

.tool-tip::before {
  width: 0;
  height: 0;
  content: "";
}

.tool-tip::before,
.tool-tip::after {
  position: absolute;
  transition: opacity 250ms ease 0ms, transform 250ms ease 0ms;
  transform-style: preserve-3d;
  opacity: 0;
  z-index: -1;
}

.tool-tip[data-tooltip-position="top"]::after,
.tool-tip[data-tooltip-position="bottom"]::after {
  left: 50%;
}

.tool-tip[data-tooltip-position="top"]::after {
  transform: translate3d(-50%, 10px, 0);
}

.tool-tip[data-tooltip-position="bottom"]::after {
  transform: translate3d(-50%, -10px, 0);
}

.tool-tip[data-tooltip-position="top"]::after {
  bottom: calc(100% + 10px);
}

.tool-tip[data-tooltip-position="bottom"]::after {
  top: calc(100% + 10px);
}

.tool-tip[data-tooltip-position="left"]::after,
.tool-tip[data-tooltip-position="right"]::after {
  top: 50%;
}

.tool-tip[data-tooltip-position="left"]::after {
  transform: translate3d(10px, -50%, 0);
}

.tool-tip[data-tooltip-position="right"]::after {
  transform: translate3d(-10px, -50%, 0);
}

.tool-tip[data-tooltip-position="left"]::after {
  right: calc(100% + 10px);
}

.tool-tip[data-tooltip-position="right"]::after {
  left: calc(100% + 10px);
}

/* Pointers */

.tool-tip[data-tooltip-position="top"]::before,
.tool-tip[data-tooltip-position="bottom"]::before {
  border-left: 7px solid transparent;
  border-right: 7px solid transparent;
  left: 50%;
}

.tool-tip[data-tooltip-position="top"]::before {
  transform: translate3d(-50%, 10px, 0);
}

.tool-tip[data-tooltip-position="bottom"]::before {
  transform: translate3d(-50%, -10px, 0);
}

.tool-tip[data-tooltip-position="top"]::before {
  border-top: 7px solid #323a45;
  bottom: calc(100% + 3px);
}

.tool-tip[data-tooltip-position="bottom"]::before {
  border-bottom: 7px solid #323a45;
  top: calc(100% + 3px);
}

.tool-tip[data-tooltip-position="left"]::before,
.tool-tip[data-tooltip-position="right"]::before {
  border-top: 7px solid transparent;
  border-bottom: 7px solid transparent;
  top: 50%;
}

.tool-tip[data-tooltip-position="left"]::before {
  transform: translate3d(10px, -50%, 0);
}

.tool-tip[data-tooltip-position="right"]::before {
  transform: translate3d(-10px, -50%, 0);
}

.tool-tip[data-tooltip-position="left"]::before {
  border-left: 7px solid #323a45;
  right: calc(100% + 3px);
}

.tool-tip[data-tooltip-position="right"]::before {
  border-right: 7px solid #323a45;
  left: calc(100% + 3px);
}

.tool-tip:hover::before,
.tool-tip:hover::after {
  opacity: 1;
  z-index: 100;
}

.tool-tip[data-tooltip-position="top"]:hover::before,
.tool-tip[data-tooltip-position="bottom"]:hover::before,
.tool-tip[data-tooltip-position="top"]:hover::after,
.tool-tip[data-tooltip-position="bottom"]:hover::after {
  transform: translate3d(-50%, 0px, 0);
}

.tool-tip[data-tooltip-position="left"]:hover::before,
.tool-tip[data-tooltip-position="right"]:hover::before,
.tool-tip[data-tooltip-position="left"]:hover::after,
.tool-tip[data-tooltip-position="right"]:hover::after {
  transform: translate3d(0px, -50%, 0);
}
</style>
