<template>
  <input :value="value" @input="updateInput" class="input" type="text" />
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'custom-input',
  props: {
    value: [String, Number],
  },
  methods: {
    updateInput(e: Event) {
      this.$emit('update:value', (e.target as any).value);
    },
  },
});
</script>

<style lang="scss" scoped>
.input {
  width: 100%;
  border: 1px solid $main-color;
  padding: 10px 15px;
  margin-top: 15px;
}
</style>
