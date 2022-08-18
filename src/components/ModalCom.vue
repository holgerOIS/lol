<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <slot></slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  components: {},
  props: ["theme"],

  methods: {
    closeModal() {
      console.log("Close?");
      this.$emit("close");
    },
  },
};
</script>
<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}

.modal p {
  font-style: italic;
}
.modal.sale {
  background: crimson;
  color: white;
}
</style>
