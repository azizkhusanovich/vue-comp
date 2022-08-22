<template>
  <button class="btn" @click="$emit('func')" :class="otherClasses">
    <slot />
  </button>
</template>

<script>
export default {
  props: ["otherClasses", "btnText"],
  emits: ["func"],
};
</script>

<style>
</style>