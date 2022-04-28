<template>
  <div v-if="!loading && task">
    <h3>{{ task.text }}</h3>
    <p>{{ task.day }}</p>
    <p>Reminder {{ task.reminder ? "Yes" : "No" }}</p>
  </div>
  <h3 v-else>Loading...</h3>
  <Button
    @onClick="goPreviousPage"
    text="Go Back"
    color="black"
  />
</template>

<script>
import Button from "../components/Button";

export default {
  name: "Task",
  props: {
    showAddTask: Boolean,
  },
  components: {
    Button,
  },
  data() {
    return {
      task: {},
      loading: true,
    };
  },
  methods: {
    goPreviousPage() {
      this.$router.back();
    },
    async fetchTask(id) {
      const res = await fetch(`/api/tasks/${id}`);
      const data = await res.json();
      this.loading = false;
      return data;
    },
  },
  async created() {
    this.task = await this.fetchTask(this.$route.params.id);
  },
};
</script>

<style scoped>
</style>