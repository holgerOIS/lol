<template>
  <h1>{{ title }}</h1>
  <p>Welcome.....</p>
  <teleport to=".modals" v-if="showModal">
    <ModalCom theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="www.google.com">Hallo</a>
      </template>
      <h1>Ninja Giveaway</h1>
      <h2>was geht ab?</h2>
    </ModalCom>
  </teleport>
  <button @click="toggleModal">show Modal</button>
  <my-caroussel>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="andresDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="andresDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="andresDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
    <div class="imageDiv"></div>
  </my-caroussel>
</template>

<script>
import ModalCom from "./components/ModalCom.vue";
import MyCaroussel from "./components/myCaroussel.vue";
export default {
  name: "App",
  components: { ModalCom, MyCaroussel },
  data() {
    return {
      title: "My first Vue App",
      header: "Sign for Giveaway",
      text: "Grab your ninja blah",
      showModal: false,
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.imageDiv {
  margin: 10px;
  display: inline-block;
  width: 200px;
  height: 150px;
  border: 1px solid blue;
  border-radius: 4px;
  background-color: #fff;
}
.andresDiv {
  margin: 10px;
  display: inline-block;
  width: 300px;
  height: 200px;

  border-radius: 4px;
  background-color: teal;
}
</style>
