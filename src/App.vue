<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <h2>Course Name</h2>
  <h3>Courses Selected: {{ count }}</h3>
  <div class="courses">
    <CourseItem
      v-for="course in courses"
      :course="course"
      :key="course.id"
      @count-to-parent="addOne"
      @remove-from-parent="removeOne"
    >
    </CourseItem>
  </div>
</template>

<script>
import CourseItem from "./components/CourseItem.vue";

export default {
  name: "App",
  data() {
    return {
      count: 0,
      courses: [
        {
          name: "Mathh",
          credit: "50",
          id: 1,
          description: "Winter Course",
          hours: 25,
          spaces: 20,
          location: "online",
          instructor: "John Doe",
        },
        {
          name: "Physi",
          credit: "50",
          id: 2,
          description: "Winter Course",
          hours: 30,
          location: "Saint Laurent Campus",
          spaces: 14,
          instructor: "Jane from the block",
        },
        {
          name: "Geogr",
          credit: "50",
          id: 3,
          description: "Winter Course",
          hours: 35,
          location: "Downtown Campus",
          spaces: 0,
          instructor: "Marie Curie",
        },
        {
          name: "WebGr",
          credit: "50",
          id: 4,
          description: "Winter Course",
          hours: 40,
          location: "online",
          spaces: 10,
          instructor: "Barbara McClintock",
        },
      ],
    };
  },
  components: {
    CourseItem,
  },
  methods: {
    addOne() {
      this.count++;
    },
    removeOne() {
      this.count--;
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.courses {
  display: flex;
  justify-items: center;
  align-items: center;
  justify-content: space-around;
}
</style>
