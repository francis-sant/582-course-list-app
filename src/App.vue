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
        {
          name: "UX Design",
          credit: "50",
          id: 4,
          description: "Leardn UX-UI principles",
          hours: 40,
          location: "Vanier I Campus",
          spaces: 10,
          instructor: "Barbara Mctoshi",
        },
        {
          name: "Introduction to Graphic Design",
          credit: "50",
          id: 10,
          description: "Learn the basics of graphic design",
          hours: 20,
          location: "Downtown Campus",
          spaces: 22,
          instructor: "Paul Rand",
        },
        {
          name: "Introduction to Web Design",
          credit: "50",
          id: 11,
          description: "Learn the basics of web design",
          hours: 20,
          location: "Downtown Campus",
          spaces: 7,
          instructor: "Paul Rand",
        },
        {
          name: "Data Science and Analytics",
          credit: "50",
          id: 9,
          description: "Explore data science and analytics tools",
          hours: 45,
          location: "Online",
          spaces: 20,
          instructor: "Ada Lovelace",
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
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  grid-gap: 20px;
  justify-items: center;
  align-items: center;
}
</style>
