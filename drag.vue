<template>
  <grid-layout
            :layout="layout"
            :col-num="12"
            :row-height="30"
            :is-draggable="true"
            :is-resizable="true"
            :vertical-compact="true"
            :margin="[10, 10]"
            :use-css-transforms="true"
            @layout-updated="layoutUpdatedEvent"
    >

        <grid-item v-for="item in layout" :key="item.i"
                   :x="item.x"
                   :y="item.y"
                   :w="item.w"
                   :h="item.h"
                   :i="item.i"
                   @resize="resizeEvent"
                   @move="moveEvent"
                   @resized="resizedEvent"
                   @moved="movedEvent">
            {{item.i}}
            <h1>ztopia</h1>
            
        </grid-item>
    </grid-layout>
</template>

<script>
import VueGridLayout from "vue-grid-layout";

var testLayout = [
  { x: 0, y: 0, w: 2, h: 2, i: "0", resizable: true, draggable: true },
  { x: 2, y: 0, w: 2, h: 4, i: "1", resizable: true, draggable: true },
  { x: 4, y: 0, w: 2, h: 5, i: "2", resizable: true, draggable: true },
  { x: 6, y: 0, w: 2, h: 3, i: "3", resizable: true, draggable: true },
  { x: 8, y: 0, w: 2, h: 3, i: "4", resizable: true, draggable: true },
  { x: 10, y: 0, w: 2, h: 3, i: "5", resizable: true, draggable: true },
  { x: 0, y: 5, w: 2, h: 5, i: "6", resizable: true, draggable: true },
  { x: 2, y: 5, w: 2, h: 5, i: "7", resizable: true, draggable: true },
  { x: 4, y: 5, w: 2, h: 5, i: "8", resizable: true, draggable: true },
  { x: 6, y: 4, w: 2, h: 4, i: "9", resizable: true, draggable: true },
  { x: 8, y: 4, w: 2, h: 4, i: "10", resizable: true, draggable: true },
  { x: 10, y: 4, w: 2, h: 4, i: "11", resizable: true, draggable: true },
  { x: 0, y: 10, w: 2, h: 5, i: "12", resizable: true, draggable: true },
  { x: 2, y: 10, w: 2, h: 5, i: "13", resizable: true, draggable: true },
  { x: 4, y: 8, w: 2, h: 4, i: "14", resizable: true, draggable: true },
  { x: 6, y: 8, w: 2, h: 4, i: "15", resizable: true, draggable: true },
  { x: 8, y: 10, w: 2, h: 5, i: "16", resizable: true, draggable: true },
  { x: 10, y: 4, w: 2, h: 2, i: "17", resizable: true, draggable: true },
  { x: 0, y: 9, w: 2, h: 3, i: "18", resizable: true, draggable: true },
  { x: 2, y: 6, w: 2, h: 2, i: "19", resizable: true, draggable: true }
];
var GridLayout = VueGridLayout.GridLayout;
var GridItem = VueGridLayout.GridItem;

export default {
  data() {
    return {
      layout: testLayout
    };
  },
  components: {
    GridLayout,
    GridItem
  },
  methods: {
    layoutUpdatedEvent: function(newLayout) {
      console.log("Updated layout: ", newLayout);
    },
    moveEvent: function(i, newX, newY) {
      console.log("MOVE i=" + i + ", X=" + newX + ", Y=" + newY);
    },
    movedEvent: function(i, newX, newY) {
      console.log("MOVED i=" + i + ", X=" + newX + ", Y=" + newY);
    },
    resizeEvent: function(i, newH, newW, newHPx, newWPx) {
      console.log(
        "RESIZE i=" +
          i +
          ", H=" +
          newH +
          ", W=" +
          newW +
          ", H(px)=" +
          newHPx +
          ", W(px)=" +
          newWPx
      );
    },
    resizedEvent: function(i, newH, newW, newHPx, newWPx) {
      console.log(
        "RESIZED i=" +
          i +
          ", H=" +
          newH +
          ", W=" +
          newW +
          ", H(px)=" +
          newHPx +
          ", W(px)=" +
          newWPx
      );
    }
  }
};
</script>

<style>
/*** EXAMPLE ***/
#content {
  width: 100%;
}

.vue-grid-layout {
  background: #eee;
}

.layoutJSON {
  background: #ddd;
  border: 1px solid black;
  margin-top: 10px;
  padding: 10px;
}

.eventsJSON {
  background: #ddd;
  border: 1px solid black;
  margin-top: 10px;
  padding: 10px;
  height: 100px;
  overflow-y: scroll;
}

.columns {
  -moz-columns: 120px;
  -webkit-columns: 120px;
  columns: 120px;
}

.vue-resizable-handle {
  z-index: 5000;
  position: absolute;
  width: 20px;
  height: 20px;
  bottom: 0;
  right: 0;
  background: url("data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBzdGFuZGFsb25lPSJubyI/Pg08IS0tIEdlbmVyYXRvcjogQWRvYmUgRmlyZXdvcmtzIENTNiwgRXhwb3J0IFNWRyBFeHRlbnNpb24gYnkgQWFyb24gQmVhbGwgKGh0dHA6Ly9maXJld29ya3MuYWJlYWxsLmNvbSkgLiBWZXJzaW9uOiAwLjYuMSAgLS0+DTwhRE9DVFlQRSBzdmcgUFVCTElDICItLy9XM0MvL0RURCBTVkcgMS4xLy9FTiIgImh0dHA6Ly93d3cudzMub3JnL0dyYXBoaWNzL1NWRy8xLjEvRFREL3N2ZzExLmR0ZCI+DTxzdmcgaWQ9IlVudGl0bGVkLVBhZ2UlMjAxIiB2aWV3Qm94PSIwIDAgNiA2IiBzdHlsZT0iYmFja2dyb3VuZC1jb2xvcjojZmZmZmZmMDAiIHZlcnNpb249IjEuMSINCXhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHhtbDpzcGFjZT0icHJlc2VydmUiDQl4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjZweCIgaGVpZ2h0PSI2cHgiDT4NCTxnIG9wYWNpdHk9IjAuMzAyIj4NCQk8cGF0aCBkPSJNIDYgNiBMIDAgNiBMIDAgNC4yIEwgNCA0LjIgTCA0LjIgNC4yIEwgNC4yIDAgTCA2IDAgTCA2IDYgTCA2IDYgWiIgZmlsbD0iIzAwMDAwMCIvPg0JPC9nPg08L3N2Zz4=");
  background-position: bottom right;
  padding: 0 3px 3px 0;
  background-repeat: no-repeat;
  background-origin: content-box;
  box-sizing: border-box;
  cursor: se-resize;
}

.vue-grid-item:not(.vue-grid-placeholder) {
  background: #ccc;
  border: 1px solid black;
}

.vue-grid-item.resizing {
  opacity: 0.9;
}

.vue-grid-item.static {
  background: #cce;
}

.vue-grid-item .text {
  font-size: 24px;
  text-align: center;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
  height: 100%;
  width: 100%;
}

.vue-grid-item .no-drag {
  height: 100%;
  width: 100%;
}

.vue-grid-item .minMax {
  font-size: 12px;
}

.vue-grid-item .add {
  cursor: pointer;
}

.vue-draggable-handle {
  position: absolute;
  width: 20px;
  height: 20px;
  top: 0;
  left: 0;
  background: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='10' height='10'><circle cx='5' cy='5' r='5' fill='#999999'/></svg>")
    no-repeat;
  background-position: bottom right;
  padding: 0 8px 8px 0;
  background-repeat: no-repeat;
  background-origin: content-box;
  box-sizing: border-box;
  cursor: pointer;
}
</style>
