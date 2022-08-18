<template>
  <div id="carcon" @click="lol">
    <slot></slot>
  </div>
  <div id="scrollerOut">
    <div id="scroller" @click="clickedOuter">
      <div
        id="scroller_innen"
        @mousedown="md = true"
        @mouseup="md = false"
        @mouseleave="md = false"
        @mousemove="clickedInner"
      ></div>
    </div>
  </div>
  <!-- <p>{{ loller }}</p> -->
  <!-- <button @click="scrollLeft">-></button>
  <button @click="scrollRight">-></button> -->
  <!-- <h1>{{ md }}</h1> -->

  <div>
    {{ test1 }}
  </div>
</template>
<script>
export default {
  components: {},
  computed: {
    test1() {
      if (document.getElementById("carcon")) {
        console.log("okokok");
        return document.getElementById("carcon").width;
      }
      return 0;
    },
  },

  data() {
    return {
      loller: "0px",
      breite: "0px",
      myColor: "",
      md: false,
    };
  },
  methods: {
    mouseleave() {
      if (this.md) {
        console.log("Bleib");
      } else {
        this.md = false;
      }
    },
    clickedInner(event) {
      if (this.md) {
        var scrollto =
          (event.x / 800) * document.getElementById("carcon").scrollWidth - 500;

        document.getElementById("carcon").scrollLeft = scrollto;
        this.lol();
      }
    },
    clickedOuter(event) {
      var scrollto =
        (event.x / 800) * document.getElementById("carcon").scrollWidth - 500;

      document.getElementById("carcon").scrollLeft = scrollto;
      this.lol();
    },
    lol() {
      this.loller =
        Math.floor(
          (document.getElementById("carcon").scrollLeft /
            document.getElementById("carcon").scrollWidth) *
            800,
          0
        ).toString() + "px";

      this.breite =
        Math.floor(
          (800 / document.getElementById("carcon").scrollWidth) * 800
        ).toString() + "px";
    },
    scrollLeft() {
      document.getElementById("carcon").scrollLeft -= 100;
      this.lol();
    },
    scrollRight() {
      document.getElementById("carcon").scrollLeft += 100;
      this.lol();
    },
    scrollToRight() {
      document.getElementById("carcon").scrollLeft += 100;
    },
  },
};
</script>
<style>
#carcon {
  margin: 20px;
  border: 1px solid grey;
  border-radius: 12px;
  width: 800px;
  height: 300px;
  top: auto;

  overflow-x: auto;
  overflow-y: hidden;
  white-space: nowrap;
}
#scrollerOut {
  margin: 20px;

  height: 60px;
  width: 800px;
}
#scroller {
  border-radius: 5px;
  margin: 0px;
  height: 2px;
  width: 800px;
  background-color: whitesmoke;
  transition: 0.5s;
}
#scrollerOut:hover #scroller {
  border-radius: 15px;
  margin: 0px;
  height: 30px;
  width: 800px;
  background-color: whitesmoke;
}
#scroller_innen {
  position: relative;
  border-radius: 15px;
  left: v-bind(loller);
  height: 100%;
  width: v-bind(breite);
  background-color: grey;
}
div::-webkit-scrollbar {
  display: none; /* for Chrome, Safari, and Opera */
}
</style>
