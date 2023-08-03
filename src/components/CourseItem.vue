<template>
  <div :class="{ 'class-selected': classFull }">
    <div class="classes">
      <div>Course Name: {{ course.name }}</div>
      <div>Description: {{ course.description }}</div>
      <div>Teacher: {{ course.instructor }}</div>
      <div>Hours: {{ course.hours }}</div>
      <div>Credits: {{ course.credit }}</div>
      <div>Location: {{ course.location }}</div>
      <div>Available Spots: {{ course.spaces + count }} /20</div>

      <div v-if="course.spaces >= 20">
        <div class="class-disabled">Course Already Full</div>
      </div>
      <div v-else-if="!classFull && course.spaces < 20">
        <button @click="addClass">Add Item</button>
      </div>
      <div v-else-if="course.spaces < 20 && course.spaces >= 0">
        <button @click="removeClass">Remove Item</button>
      </div>
    </div>
  </div>
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
      classFull: false,
    };
  },

  methods: {
    addClass() {
      this.$emit("count-to-parent");
      this.count++;
      this.classFull = true;
    },
    removeClass() {
      this.$emit("remove-from-parent");
      this.count--;
      this.classFull = false;
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

.classes {
  border: 3px solid rgb(35, 46, 139);
  text-align: center;
  font-weight: bold;
  margin: auto;
  border-radius: 10px;
  height: 300px;
  padding: 20px;
  max-height: 100%;
}

.class-selected {
  background-color: #41b883;
  color: #1041ff;
  border-radius: 10px;
}

.class-disabled {
  background-color: #cf3e3e;
  color: #fafafa;
  font-weight: bold;
  border-radius: 10px;
  padding: 7px;
}
</style>
