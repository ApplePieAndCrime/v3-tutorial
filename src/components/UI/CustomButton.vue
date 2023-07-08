<template>
  <button :class="`btn btn-${type}`"><slot></slot></button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'custom-button',
  props: {
    type: String,
  },
});
</script>

<style lang="scss" scoped>
@mixin type-color($type) {
  $color: lighten($main-color, 10);
  @if $type == 'success' {
    $color: rgb(32, 149, 32);
  } @else if $type== 'error' {
    $color: #bb2e2e;
  } @else {
  }

  background-color: $color;
  border: 2px solid darken($color, 5);
}
.btn {
  align-self: flex-end;
  padding: 10px 15px;
  color: whitesmoke;
  cursor: pointer;
  @include type-color('');
}

.btn-success {
  @include type-color('success');
}

.btn-error {
  @include type-color('error');
}
</style>
