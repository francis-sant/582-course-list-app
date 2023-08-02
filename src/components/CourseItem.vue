<template>
  <h2>Course Name</h2>
  <p>Description</p>
  <p>{{ count }}</p>
  <button @click="innerAdd">Add Inside</button>
  <button @click="outerAdd">Add outside</button>
</template>

<script>
export default {
  name: "CourseItem",
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    innerAdd() {
      this.count++;
    },
    outerAdd() {
      this.$emit("countTparent");
    },
  },
};
</script>
