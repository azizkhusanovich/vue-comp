<template>
  <ul>
    <li v-for="course in coursesList" :key="course.id">
      {{ course.title }} <span>{{ course.wasRead ? "✅" : "" }}</span>
    </li>
  </ul>
</template>

<script>
export default {
  inject: ["coursesList"],
};
</script>

<style>
</style>