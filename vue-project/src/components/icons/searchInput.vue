<template>
  <div>
    <input @input="onChange" type="text" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SearchInput",
  methods: {
    onChange: function (event) {
      // const term = event.target.value
      this.$emit("newTerm", (event.target as HTMLInputElement).value);
    },
  },
});
</script>
