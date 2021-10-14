<template>
  <h1>{{ title }}</h1>
  <div>
    <input type="text" ref="name" />
    <br />
    <button @click="handleClick">Click</button>
  </div>
  <Modal v-if="showModal" :theme="theme" @close="toggleModal">
    <template v-slot:links>
      <a href="#">Sign me up!</a>
    </template>
    <h1>Sign Up for Giveaways</h1>
    <p>
      Get the latest updates as soon as we give them away
    </p>
  </Modal>
  <button @click="toggleModal">Show modal</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My first App",
      theme: "sales",
      showModal: false,
    };
  },
  methods: {
    handleClick() {
      this.$refs.name.classList.add("anotherclass");
      this.$refs.name.focus();
    },
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
</style>
