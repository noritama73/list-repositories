<template>
  <button @click="getUserRepos()">GET</button>
  <div v-for="repo in repos" :key="repo">{{ repo }}</div>
</template>

<script lang="ts">
import FetchRepositories from "@/components/FetchRepositories.vue";
import { ref, defineComponent } from "vue";

export default defineComponent({
  props: {
    user: {
      type: String,
      required: true,
    },
  },
  setup(props) {
    const repos = ref<string[]>([]);
    const getUserRepos = async () => {
      let res = await FetchRepositories.listRepos(props.user);
      repos.value = res.data.map((r) => r.full_name);
    };
    return {
      repos,
      getUserRepos,
    };
  },
});
</script>
