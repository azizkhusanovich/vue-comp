<template>
  <div class="card">
    <h2>{{ title }}</h2>

    <button-card @func="open" :otherClasses="isNewOpen ? 'danger' : ''">
      {{ isNewOpen ? "Yopish" : "Batafsil" }}
    </button-card>

    <button-card
      otherClasses="danger"
      v-if="wasRead"
      @func="$emit('reject', this.id)"
    >
      Bekor qilish
    </button-card>

    <div v-if="isNewOpen">
      <p>
        {{ text }}
      </p>

      <button-card otherClasses="primary" v-if="!wasRead" @func="read">
        Tanishdim
      </button-card>

      <CourseList />
    </div>
  </div>
</template>

<script>
import ButtonCard from "./ButtonCard.vue";
import CourseList from "./CoursesList.vue";
export default {
  data() {
    return {
      isNewOpen: this.isOpen,
    };
  },
  //   props: ["title", "text", "is-open", "was-read"],
  props: {
    id: {
      type: Number,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
    "is-open": {
      type: Boolean,
      required: false,
      default: false,
    },
    "was-read": {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  emits: ["open", "read", "reject"],
  methods: {
    open() {
      this.isNewOpen = !this.isNewOpen;
      if (this.isNewOpen) {
        this.$emit("open");
      }
    },
    read() {
      this.isNewOpen = false;
      this.$emit("read", this.id);
    },
  },
  components: {
    ButtonCard,
    CourseList,
  },
};
</script>

<style>
</style>