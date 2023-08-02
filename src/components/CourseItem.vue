<template>
  <div>Course Name: {{ course.name }}</div>
  <div>Description: {{ course.description }}</div>
  <div>Teacher: {{ course.instructor }}</div>
  <div>Hours: {{ course.hours }}</div>
  <div>Credits: {{ course.credit }}</div>

  <!-- <button>Add Item</button> -->
  <!-- <button @click="innerAdd">Add Item</button> -->
  <button @click="outerAdd">Add outside</button>
</template>

<script>
export default {
  name: "CourseItem",
  props: {
    course: {
      type: Object,
      required: true,
    },
  },

  data() {
    return {
      count: 0,
      b: false,
    };
  },

  methods: {
    innerAdd() {
      this.count++;
    },
    outerAdd() {
      this.$emit("count-to-parent");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h2 {
  margin-bottom: 2rem;
}

h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

div {
  margin-bottom: 1rem;
}
</style>
