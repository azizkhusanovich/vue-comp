<template>
  <div class="container">
    <div class="card">
      <h2>Slots</h2>

      <app-slots>
        <template v-slot:text>
          <p>
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Autem sunt
            numquam ea qui commodi eos quaerat ipsa. Distinctio, eveniet labore?
          </p>
        </template>

        <template #title>
          <h2>Title</h2>
        </template>

        <template #footer>
          <p>Footer</p>
        </template>

        <template #items="{ iter }">
          <div class="item">
            <p style="color: green">{{ iter }}</p>
          </div>
        </template>
      </app-slots>
    </div>
  </div>
</template>
        
<script>
import AppSlots from "./components/AppSlots.vue";
export default {
  components: {
    AppSlots,
  },
};
</script>

<style>
</style>