<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <teleport to="#modals" v-if="showModal">
    <!-- eslint-disable-next-line -->
    <CustomModal :header="header" :text="text" theme="sale" @close="toggleModal">
      <h2>Ninja Giveways!</h2>
      <p>Grab ur ninja stuff</p>
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
    </CustomModal>
  </teleport>
  <button @click.shift="toggleModal">Show modal (shift)</button>

  <teleport to="#modals" v-if="showModalII">
    <!-- eslint-disable-next-line -->
    <CustomModal :header="header" :text="text" @close="toggleModalII"></CustomModal>
  </teleport>
  <button @click="toggleModalII">Show modal</button>
  <br />
  <br />
  <input type="text" ref="name" />
  <button @click="handleClick">click me daddy</button>
</template>

<script>
import CustomModal from "./components/CustomModal.vue";

export default {
  name: "App",
  components: { CustomModal },
  data() {
    return {
      title: "My first Vue App :)",
      header: "Sign up for special features!",
      text: "Grab ur spesial giveaways!",
      showModal: false,
      showModalII: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalII() {
      this.showModalII = !this.showModalII;
    },
  },
};
</script>

<style>
#app,
#modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
