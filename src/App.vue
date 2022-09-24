<template>
  <div>
    <input v-model="username" placeholder="GitHub User" key="username" />
    <p>{{ username }}</p>
    <UserRepositories :user="username"></UserRepositories>
  </div>
</template>

<script lang="ts">
import UserRepositories from "@/components/UserRepositories.vue";
import { ref, defineComponent } from "vue";

export default defineComponent({
  name: "App",
  components: {
    UserRepositories,
  },
  setup() {
    const username = ref<string>("");
    return {
      username,
    };
  },
});
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
