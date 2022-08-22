<template>
  <div class="container pt-1">
    <div class="card">
      <h1>Front-End kurslari haqida ma'lumot</h1>
      <span>Ko'rildi: {{ counter }} <br /> </span>
      <span>Tanishildi: {{ countRead }} </span>
    </div>

    <course-card
      v-for="course in courses"
      :key="course.id"
      :title="course.title"
      :id="course.id"
      :text="course.text"
      :was-read="course.wasRead"
      :is-open="isOpen"
      @open="addCount"
      @read="readRate"
      @reject="rejectRate"
    ></course-card>
  </div>
</template>

<script>
import CourseCard from "./components/CourseCard";

export default {
  data() {
    return {
      isOpen: false,
      countRead: 0,
      counter: 0,
      courses: [
        {
          id: 1,
          title: "HTML",
          wasRead: false,
          text: " Lorem ipsum dolor sit amet consectetur, adipisicing elit. Ut ab voluptatum distinctio explicabo modi reprehenderit?",
        },
        {
          id: 2,
          title: "CSS",
          wasRead: false,
          text: " Lorem ipsum dolor sit amet consectetur, adipisicing elit. Ut ab voluptatum distinctio explicabo modi reprehenderit?",
        },
        {
          id: 3,
          title: "JavaScript",
          wasRead: false,
          text: " Lorem ipsum dolor sit amet consectetur, adipisicing elit. Ut ab voluptatum distinctio explicabo modi reprehenderit?",
        },
        {
          id: 4,
          title: "VueJS",
          wasRead: false,
          text: " Lorem ipsum dolor sit amet consectetur, adipisicing elit. Ut ab voluptatum distinctio explicabo modi reprehenderit?",
        },
      ],
    };
  },
  components: { CourseCard },
  methods: {
    addCount() {
      this.counter++;
    },
    readRate(id) {
      const elemIndex = this.courses.findIndex((elem) => elem.id === id);
      this.courses[elemIndex].wasRead = true;
      this.countRead++;
    },
    rejectRate(id) {
      const element = this.courses.find((elem) => elem.id === id);
      element.wasRead = false;
      this.countRead--;
    },
  },
  provide() {
    return {
      coursesList: this.courses,
    };
  },
};
</script>

<style>
</style>