<template>
  <h1>{{ title }}</h1>
  <div>
    <input type="text" ref="name" />
    <br />
    <button @click="handleClick">Click</button>
  </div>
  <Modal v-if="showModal" :header="header" :text="text" :theme="theme" @close="toggleModal" />
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
      header: "Sign Up for Giveaways",
      text: "Get the latest updates as soon as we give them away nowwww",
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
