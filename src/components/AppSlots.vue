<template>
  <div class="card">
    <slot name="title"></slot>
    <slot name="text"></slot>
    <div v-if="$slots.footer">
      <slot name="footer"></slot>
    </div>

    <ul>
      <li v-for="item of 5" :key="item">
        <slot name="items" v-bind:iter="item"></slot>
      </li>
    </ul>
    
  </div>
</template>

<script>
export default {
  mounted() {
    console.log(this.$slots);
  },
};
</script>

<style>
</style>