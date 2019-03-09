<template>
  <div>
    <span>
      Lesson 19 was the last
    </span>
    <div
      class="loading"
      v-if="loading"
    >
      Loading...
    </div>
    <h2>Home</h2>
    <ul
      v-for="post in posts"
      :key="post._id"
    >
      <li>
        {{post.title}}
        {{post.imageUrl}}
      </li>
    </ul>
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "Home",
  created() {
    this.handleGetPosts();
  },
  computed: {
    ...mapGetters(["loading", "posts"])
  },
  methods: {
    handleGetPosts() {
      // Vuex store action
      this.$store.dispatch("getPosts");
    }
  }
};
</script>