<template>
  <h1>{{ title }}</h1>
  <div>
    <input type="text" ref="name" />
    <br />
    <button @click="handleClick">Click</button>
  </div>

  <br />
  <button @click="toggleModal">Show modal</button>
  <br />
  <br />
  <button @click.alt="toggleModalTwo">Show my modal(alt)</button>

  <!-- Modals -->
  <teleport to=".modals" v-if="showModal">
    <Modal :theme="theme" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign me up!</a>
      </template>
      <h1>Sign Up for Giveaways</h1>
      <p>
        Get the latest updates as soon as we give them away
      </p>
    </Modal>
  </teleport>
  <teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <template v-slot:links>
        <a href="#">Sign me up!</a>
      </template>
      <h1>How to reuse a modal</h1>
      <p>
        This is the way we reuse the modal template
      </p>
    </Modal>
  </teleport>
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
      showModalTwo: false,
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
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
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
