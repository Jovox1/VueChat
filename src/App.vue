<template>
  <div class="messagers">
    <div class="messagers__window">
      <WindowHeader :src="'alex'" :name="'Александр'" :status="'Онлайн'" />
      <WindowBody :sendId="2" :message="message" />
      <WindowFooter :sendId="2" @new-mess="newMess" />
    </div>
    <div class="messagers__window">
      <WindowHeader :src="'jane'" :name="'Евгений'" :status="'Онлайн'" />
      <WindowBody :sendId="1" :message="message" />
      <WindowFooter :sendId="1" @new-mess="newMess" />
    </div>
  </div>
</template>

<script>
import WindowBody from "./components/WindowBody.vue";
import WindowFooter from "./components/WindowFooter.vue";
import WindowHeader from "./components/WindowHeader.vue";

export default {
  name: "App",
  components: {
    WindowHeader,
    WindowBody,
    WindowFooter,
  },
  data() {
    return {
      message: [],
    };
  },
  created() {
    const messStorage = localStorage.message
      ? JSON.parse(localStorage.message)
      : [];
    this.message = messStorage;
  },
  methods: {
    newMess(mess) {
      this.message.push(mess);
      localStorage.message = JSON.stringify(this.message);
    },
  },
};
</script>

<style></style>
