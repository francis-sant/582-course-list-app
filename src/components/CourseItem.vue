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
      <!-- <button>Add Item</button> -->
      <!-- <button @click="innerAdd">Add Item</button> -->
      <!-- <button @click="outerAdd">Add outside</button> -->

      <div v-if="!classFull && course.spaces < 20">
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
    // outerAdd() {
    //   this.$emit("count-to-parent");
    // },
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
  margin: auto;
  border-radius: 10px;
  height: 300px;
  padding: 20px;
}

.class-selected {
  background-color: #41b883;
  color: #264c75;
  font-weight: bold;
  border-radius: 10px;
}

.class-disabled {
  background-color: #f5f5f5;
  color: #c4c4c4;
  font-weight: bold;
  border-radius: 10px;
}
</style>
