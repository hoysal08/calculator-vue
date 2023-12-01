<template>
  <div id="app">
    <h1>Calculator</h1>
    <input-fields />
  </div>
</template>

<script>
import InputFields from "./components/InputFields.vue";

export default {
  components: {
    InputFields,
  },
};
</script>